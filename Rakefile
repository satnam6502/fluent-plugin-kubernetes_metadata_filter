require "bundler/gem_tasks"
require "rake/testtask"
require "bump/tasks"

task :test => [:base_test]

task :default => [:test, :build]

desc 'Run test_unit based test'
Rake::TestTask.new(:base_test) do |t|
  # To run test for only one file (or file path pattern)
  #  $ bundle exec rake base_test TEST=test/test_specified_path.rb
  #  $ bundle exec rake base_test TEST=test/test_*.rb
  t.libs << "test"
  t.test_files = Dir["test/**/test_*.rb"].sort
  t.verbose = true
  #t.warning = true
end

desc "Add copyright headers"
task :headers do
  require 'rubygems'
  require 'copyright_header'

  args = {
    :license => 'ASL2',
    :copyright_software => 'Fluentd Kubernetes Metadata Filter Plugin',
    :copyright_software_description => "Enrich Fluentd events with Kubernetes metadata",
    :copyright_holders => ['Red Hat, Inc.'],
    :copyright_years => ['2015'],
    :add_path => 'lib:test',
    :output_dir => '.'
  }

  command_line = CopyrightHeader::CommandLine.new( args )
  command_line.execute
end
