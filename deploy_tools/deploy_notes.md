Provisioning a new site
========================

## Required packages:

* nginx
* python3
* Git
* pip
* gunicorn
* virtualenv

eg, on Ubuntu:

	sudo apt-get install nginx git python3 python3-pip
	sudo pip3 install virtualenv gunicorn

## Nginx config

* see nginx.conf
* To start nginx service:
	- Run:

		sudo service nginx start

	- Put a nginx.conf file in /etc/nginx/sites-available
	- Put a symlink in /etc/nginx/sites-enabled and link it to the nginx.conf file
	- Run:

	sudo service nginx reload

## Start gunicorn:

* install gunicorn in virtualenv
* Run:
	path/to/virtualenv/gunicorn --bind unix.socket projectname.wsgi:application
* The upper command can be run automatically by systemd

## Systemd config

* see gunicorn-systemd.service
* In version 15.0.1 and later, ubuntu uses systemd to replace upstart.
* To start and stop gunicorn with systemd:
	- Put a config file like gunicorn-systemd.service file in /etc/systemd/system/;
	- Run:

	sudo systemctl start gunicorn-systemd
	sudo systemctl enable gunicorn-systemd


