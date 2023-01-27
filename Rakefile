require "bundler/gem_tasks"

require "cucumber/rake/task"
Cucumber::Rake::Task.new(:cucumber)

require "rspec/core/rake_task"
RSpec::Core::RakeTask.new(:spec)

task :default => [:spec, :cucumber]

require 'rdoc/task'
Rake::RDocTask.new do |rd|
  rd.main = "README.md"
  rd.rdoc_files.include("README.md", "lib/**/*.rb")
end

require 'rubygems/package_task'
require 'rspec/core/rake_task'

$: << File.join(File.dirname(__FILE__),'lib')
require 'stitch_fix/y/tasks'

include Rake::DSL

gemspec = Gem::Specification.load('stitchfix-test-gem.gemspec')
Gem::PackageTask.new(gemspec) {}
RSpec::Core::RakeTask.new(:spec)
StitchFix::Y::ReleaseTask.for_rubygems(gemspec)
StitchFix::Y::VersionTask.for_rubygems(gemspec)

task :default => :spec

