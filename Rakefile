# frozen_string_literal: true

require "bundler/setup"
require "bundler/gem_tasks"
require "rake/testtask"
require "rubocop/rake_task"

desc "Test pl_fustigit"
namespace :test do
  Rake::TestTask.new(:spec) do |test|
    test.libs << "spec"
    test.pattern = "spec/**/*_spec.rb"
    test.verbose = false
    test.warning = false
  end

  desc "Test pl_fustigit and calculate test coverage"
  task :coverage do
    ENV["COVERAGE"] = "true"
    Rake::Task["test:spec"].invoke
  end
end

desc "Run RuboCop"
RuboCop::RakeTask.new(:rubocop) do |task|
  task.options << "--display-cop-names"
end

desc "Run all spec tests and linters"
task check: %w[test:spec rubocop]

task default: :check
