require 'jekyll'


# Change your GitHub reponame
GITHUB_REPONAME = "xautjzd/jekylltest"

desc "Generate blog files"
task :generate do
    Jekyll::Site.new(Jekyll.configuration({
        "source"      => ".",
        "destination" => "_site"
    })).process
end


desc "Generate and publish blog to gh-pages"
task :publish => [:generate] do
    # puts "Deploying branch to Github Pages "
    # cd "_site" do
    #     system "git init"
    #     system "git add ."
    #     puts "\n## Commiting: Site updated at #{Time.now.utc}"
    #     message = "Site updated at #{Time.now.utc}"
    #     system "git commit -m #{message.inspect}"
    #     system "git remote add origin https://www.github.com/#{GITHUB_REPONAME}.git"
    #     system "git push origin master:/refs/heads/gh-pages --force"
    #     puts "\n## Github Pages deploy complete."
    # end

    Dir.mktmpdir do |tmp|
        cp_r "_site/.", tmp

        pwd = Dir.pwd
        Dir.chdir tmp

        system "git init"
        system "git add ."
        message = "Site updated at #{Time.now.utc}"
        system "git commit -m #{message.inspect}"
        system "git remote add origin https://www.github.com/#{GITHUB_REPONAME}.git"
        # system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
        system "git push origin gh-pages --force"

        Dir.chdir pwd
    end
end
