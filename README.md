this is linux automation login # shellscripting-TUI

#!/bin/bash
dialog  --infobox  "      ~~~~***WELCOME TO ONE CLICK LINUX ***~~~~"  5  60
sleep 2

Login()
{
	dialog   --inputbox     "USERNAME: "   10  30    2>/tmp/un.txt
	dialog   --passwordbox  "PASSWORD: "   10  30    2>/tmp/pd.txt




	u=`cat  /tmp/un.txt`
	p=`cat /tmp/pd.txt`
	
	rm /tmp/un.txt
	rm /tmp/pd.txt

	if   [  $u == "linux" -a $p == "lw" ] 
	then
		dialog  --infobox  "           WELCOME USER " 5  60
		sleep 2
		bash   menu.sh
	else
		dialog  --infobox  "           Please ensure you have entered correct Username and Password"  5  90
		sleep 2
		dialog   --yesno "Want to go for Another Login Attempt"  5  40
		a=`echo  $?`
		if  [ $a -eq 0 ]
		then
		Login
		else
		killall  gnome-terminal
		fi
	fi

}
Login

