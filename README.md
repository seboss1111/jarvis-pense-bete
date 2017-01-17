<!---
IMPORTANT
=========
This README.md is displayed in the WebStore as well as within Jarvis app
Please do not change the structure of this file
Fill-in Description, Usage & Author sections
Make sure to rename the [en] folder into the language code your plugin is written in (ex: fr, es, de, it...)
For multi-language plugin:
- clone the language directory and translate commands/functions.sh
- optionally write the Description / Usage sections in several languages
-->
## Description
Ce plugin vous permet d'ajouter des items à un pense-bête et ensuite, de le recevoir par courriel

Il faut aussi installer le service ssmtp :
sudo apt-get install ssmpt
Ouvrir le fichier ssmtp.conf:
nano /etc/ssmpt/ssmtp.conf
Puis le configurer en ajoutant c'est quelque ligne avec tes infos (là c'est pour gmail):
root=adresse@gmail.com
mailhub=smtp.gmail.com:587
hostname=raspberry
AuthUser=adresse@gmail.com
AuthPass=MotDePasseGmail
FromLineOverride=YES
UseSTARTTLS=YES
Puis sauvegarder : Ctrl+X puis O pour oui et entrer

This plugin can be use to add reminders to a list and then, receive that list by email

You also need to install the ssmpt:
sudo apt-get install ssmpt
Open ssmtp.conf:
nano /etc/ssmpt/ssmtp.conf
Configure it using your email settings:
root=address@gmail.com
mailhub=smtp.gmail.com:587
hostname=raspberry
AuthUser=addrese@gmail.com
AuthPass=PasswordGmail
FromLineOverride=YES
UseSTARTTLS=YES
And then save : Ctrl+X and Y for yes and enter

## Usage
```
*PENSE (*) TERMINE*|*PENSE (*) FIN*|*PENSE (*) STOP*|*PENSE (*) ARRET*==echo "Pense(1)" >> ~/pensebete.txt && say "J'ai ajouté (1) aux pense bête"
*SUPPRIME*PENSE*|*VIDE*PENSE*==say "Veux tu confirmer la supression du pense-bête?"
>*OUI*==echo "" > ~/pensebete.txt && say "Ok les pense bête sont effacés"
>*NON*==say "OK Je ne la supprime pas"
*LI*PENSE*|*QUOI*DANS*PENSE*==say "elle contient $(cat ~/pensebete.txt)"
*ENVOI*PENSE*MAUD*|*EVOI*PENSE*MOD*==mpack -s "Contenu du pense-bête" /home/pi/pensebete.txt sonmail@gmail.com && say "Le pense-bête ont été envoyer à Maud"
*ENVOI*PENSE*==mpack -s "Contenu du pense-bête" /home/pi/pensebete.txt monmail@gmail.com && say "Le pense-bête ont été envoyer à Thomas"

*REMINDER (*) TERMINATED*|*REMINDER (*) END*|*REMINDER (*) STOP*==echo "Reminder(1)" >> ~/reminder.txt && say "I've added (1) to the reminder"
*DELETE*REMINDER*|*EMPTY*REMINDER*==say "Please confirm that you want to delete the reminders?"
>*YES*==echo "" > ~/reminder.txt && say "Ok reminders has been deleted"
>*NO*==say "OK I won't delete the reminders"
*READ*REMINDER*|*WHAT*IN*REMINDER*==say "It contains $(cat ~/reminder.txt)"
*SEND*REMINDER*MAUD*|*EMAIL*REMINDER*MOD*==mpack -s "Reminder content" /home/pi/reminder.txt sonmail@gmail.com && say "The reminder has been sent to Maud"
*SEND*REMINDER*THOMAS==mpack -s "Reminder content" /home/pi/reminder.txt monmail@gmail.com && say "The reminder has been sent to Maud Thomas"
```

## Author
[godinperson] et/and [tchoul]