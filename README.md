Bashscript
==========

Password change script

#Test.sh
#=======

#!/bin/bash

echo "Enter your choice"

echo "1.       Change Password"

echo " 2.       See the disk space"

echo "3.       Login to other box using ssh"

echo "4.       Show all Service running"

echo "5.       Show all ports opened"

echo "6.       Show all java apps running"

echo "7.       Facility to kill a  app"

echo "8.       Exit"

read choice

case "$choice" in
1)clear
echo "Enter the user name u want to change"
read user 
grep -q "$user" /etc/passwd
a=echo $?
if [ a -ne 0 ]
then 
echo "User $user does not exist."
fi
if [ "$UID" -ne "0" ]
then
echo "Only root can run this script." 
exit 111
else
echo "Enter the new password"
read NEWPASSWORD

echo "$NEWPASSWORD" | passwd --stdin "$user"
echo "User $user password changed!"
 exit 0
fi;;
2)clear
echo "disk space is:
df -hT;;
3)clear
#If already key generated
echo "Enter the user name you want to connect"
read usern
echo "Enter the hostname or IP address you want to connect"
read hostname
ssh $user@$hostname;;
4)clear
service --status-all;;
5)clear
netstat -ntlp;;
6)clear
ps aux | grep java;;
7)clear
echo "Enter the application you want to kill"
read appln
ps -ux|grep $appln |cut -d -f2 -n |kill -9;;
8)clear
exit 0;;
ease
