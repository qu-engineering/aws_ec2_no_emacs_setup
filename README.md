Copy the contents of this README.md, dump a copy into machine-setup.bash just as you log in as ubuntu for the first time,
and run this on a new EC2 instance running Ubuntu 12.04.2 LTS to configure both the machine and the environment for 
developing the CDO Seoul app:

```

#!/bin/bash
cd $HOME
sudo apt-get install -y git-core
git clone https://github.com/munair/aws_ec2_no_emacs_setup.git
./aws_ec2_no_emacs_setup/setup.sh   

# Next, create an SSH key and (by copy/pasting with the mouse)
# add it to Github at https://github.com/settings/ssh
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub

# Now you can clone via SSH from github.
# Cloning over SSH allows you to push/pull changes.
git clone https://github.com/munair/cdoseoul-com.git
git config --global user.name Munair
git config --global user.email munair@gmail.com

# Next change into the app directory and get all
# npm dependencies.
cd cdoseoul-com
npm install

# Login and add the SSH key created previously to Heroku
# Then create Heroku apps if they don't already exit.
# Add all necessary add-ons if creating Heroku apps.
heroku login
heroku keys:add

exit
# We need to logout and log back in to enable node

```

See also http://github.com/startup-class/dotfiles and
[Startup Engineering Video Lectures 4a/4b](https://class.coursera.org/startup-001/lecture/index)
for more details.





