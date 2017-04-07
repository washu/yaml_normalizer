# frozen_string_literal: true

require './tmpfix/rake_application'

require 'bundler/gem_tasks'

require 'rspec/core/rake_task'
require 'rubocop/rake_task'
require 'yard'
require 'inch/rake'

RSpec::Core::RakeTask.new(:spec)
RuboCop::RakeTask.new
YARD::Rake::YardocTask.new do |config|
  config.stats_options = ['--list-undoc', '--compact']
end
Inch::Rake::Suggest.new

desc 'Mutation testing to check mutation coverage of current RSpec test suite'
task :mutant do
  puts `bundle exec mutant --include lib \
    --require yaml_normalizer \
    --use rspec YamlNormalizer*`
end

task default: :spec
