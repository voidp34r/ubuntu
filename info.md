Command to list recently installed packages that were installed via any method (apt-get, Software Center et al.):

grep " install " /var/log/dpkg.log

You could run this command to list only the recently installed package names,

awk '$3~/^install$/ {print $4;}' /var/log/dpkg.log


If you use sudo to start apt or aptitude, all commands are written to /var/log/auth.log. So a grep apt /var/log/auth.log should give you the commands. In my case (Debian), grep '/usr/bin/apt' auth.log* | awk '{print $15}' returned all apt/aptitude commands neatly. Adjust accordingly. Good luck!
