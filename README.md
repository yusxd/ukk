apt update 
apt install apache2 php phpmyadmin mysql-server mysql-client wget unzip git -y
create database namadb;
create user 'nama'@'localhost' identified by 'ukk2024_';
grant all privileges on namadb.* to 'nama'@'localhost';
flush privileges;
wget https://wordpress.org/latest.zip
unzip latest.zip
mv wordpress/ /var/www/html
chmod 755 -R /var/www/html/wordpress
chown www-data:www-data -R /var/www/html/wordpress
git clone https://github.com/firmansyahirsyaad76/wordpress.conf.git
cp wordpress.conf/wordpress.conf /etc/apache2/sites-available/
a2dissite 000-default.conf
a2ensite wordpress.conf
a2enmod rewrite
systemctl restart apache2





