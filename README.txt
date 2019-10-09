# Git Fundamental Commands

# Git installation on linux :

Step 1 – update default packages
sudo apt-get update

Step 2 – install git
sudo apt install git

Step 3 – confirm successful installation
git --version

Step 4 – setup git username and useremail
git config --global user.name “User Name”
git config --global user.email “User Email”

If you want to see which config is where
git config --list –show-origin

If you want to set default editor for gitconfig file
git config –global core.editor nano

If you want to autocorrect the mispelled git commands
git config --global help.autocorrect 1

If you want to auto color for git ui
git config --global color.ui auto

If you want to secure your binary file , CR(window) and LF(linux)
git config --global core.autocrlf false | true | input
for window use false and for linux use input

If you need to edit this file
nano ~/.gitconfig

If you need to view git config file
cat ~/.gitconfig
git config –list

If you want to remove any config file setting 
git config --unset user.name
git config --unset core.autocrfl

Now check git config –list, these two setting will be removed.

# Working On Git :

Pre-condition – create a directory git-practice and run cd git-practice then run command ls -la to view all files in pws

Step 1 – initializing empty git repository
git init
ls -la

Step 2 – check config file of this repo 
git config --list 

You can set separate user.name for this repo as it works in hierarchy
git config user.name “Other User”

You can also remove this child user 
git config --unset user.name 

Step 3 – add README.txt file in pwd and write some text
echo “Hello, Git” > README.txt

Step 4 – to check the status of git as commits and untracked files
git status

Step 5 – adding new untracked files to git 
git add . for adding all the untracked and changed files of repo
git add README.txt

New file README.txt has been added to the staging area and ready to commit.

Step 6 – commiting the file from staging area to repo by some commit message
git commit -m “Added README.txt file”

Step 7 – use git log to check the details changes you have made including author, date of commit , commit id and changed files
git status
git log

You can see the difference of messages in console.

Step 8 – now make some changes in your files and then check status
nano README.txt 
git status

Then modified file README.txt appears. Use git add <filename> to update what will be commited and git checkout <filename> to discard changes in pwd.

Step 9 – to discard the changes made
git checkout README.txt
for multiple operations modified, deleted and added
git reset --hard
git status

Step 10 – Again make some changes in the file . Then git add <filename> to move the file in staging area then commiting the changes made git commit -m “message”
nano README.txt
git status
git add README.txt OR git add -u
git status
git commit -m “Updated README.txt File”
git log

If you mistakely ran git add -u then you can run git reset HEAD <filename>, to move the file from staging area to unstaged area after git add command (moving to staging area), then git checkout to discard the changes you have made

Step 11 – checking difference in the files you changed using commit id and also by HEAD~<1,2,3...>
git diff commit_id(first6)..comit_id(first6) or git diff HEAD~1..HEAD

Step 12 – if you want to go to previous commit or in other words you wants to revert the latest commit done then
git reset --soft HEAD~1

Now add some new files by touch temp1.txt temp2.txt
Step 13 – cleaning or removing unwanted files 
git clean -n
git clean -f

Step 14 – ignoring some files we don’t want to commit like log files which continously changes so we should ignore that files by putting it in .gitignore

# Cloning A Repo From Git :
Now we will clone a repo from the git and do some operations on this repo.

Step 1 – clonning the git repo using clone link, to clone entire project
git clone https://github.com/jquery/jquery.git

Step 2 – getting all commits which have been done since beginning
git log
For more in condensed form run this command
git log --oneline 

Step 3 – to get number to total commits done using wordcount function and counting the number of lines for git log --oneline . Using --graph to view all the brach merge details.
git log --oneline | wc -l
git log --oneline –graph

Step 4 – to get shortlog of all commits as author name, commit messages and number of commits done by particular users. Also git shortlog -sne , s for summary, n for shorting it in numerical order and e for email address
git shortlog
git shortlog -sne

Step 5 – viewing git latest commit done with details or commit by commit is or HEAD~<particula_number>
git show HEAD
git show HEAD~1

Step 6 – getting remote of the repo using git remote and git remote -v shows url for fetch and push 
git remote
git remote -v

Step 7 – in git there are mainly 4 protocols as http(s) : read-write password for auth , git : read-only, ssh : read-write ssh for auth and file : read-write locally
In pwd run, to view the config file of this repo
ls -a
cat .git/config

Step 8 – to know the number branches using git branch and git branch -r for remote branches and using git tag we can view versions as stablepoints or checkpoints
git remote
git branch
git branch -r or git branch --remote
git tag 
git tag | wc -l

# Working On Local File :
Now switch back to the local file that we have created git-practice
cd git-practice

Step 1 – checking remote and branch for this repo, we will not get any output as this repo is in our local system and not yet pushed to github cloud
git remote
git branch 
git branch -r 

Step 2 – adding remote for our local project using remote add <github_reponame> and check using git fetch and git remote -v
git remote add origin https://github.com/sumit-kumar-singh/GitFundamentals
git remote
git fetch 

Step 3 – push the changes in your local repo to the github
git push origin master

Your code has been uploaded to github. Now made some changes in one the file and commit it and run
git log
git log origin/master

You will find that the changes you made are not reflecting in github but its showing in git log locally. So we have to push the code using command
git push origin master
git log
git log origin/master

Now you will find both are in sink, pointing to master to master (HEAD -> master, origin/master)

# Pulling From A Remote :
Step 1 – Now we will take pull from remote using git pull, which is basically combination of git fetch; git merge origin/master.
git pull

Step 2 – So if you do git pull then you will get as there is no tracking information for the current branch. Please specify which branch you want to merge with. As there is no link between the master branch on github and remote origin locally. So we have to link it using these command 
git pull origin master
git branch --set-upstream-to master origin/master

Step 3 – for pushing to a remote we have to run git commit -am “Updated” and git push then cli ask to enter password and username everytime we push our changed code. So to git rid of this use ssh
git remote rm origin 
git remote -v
git remote add origin git@github.com:sumit-kumar-singh/GitFundamentals
git push


to be continued..
