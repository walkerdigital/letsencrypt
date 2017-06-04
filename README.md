# Install Let's Encrypt SSL on ServerPilot [![Ubuntu 14.04](https://img.shields.io/badge/Ubuntu-14.04-brightgreen.svg)]() [![Ubuntu 16.04](https://img.shields.io/badge/Ubuntu-16.04-brightgreen.svg)]()

Automate the installation of Let's Encrypt SSL on the free plan of ServerPilot


## Ready Your Droplet

In case you want to start over, **get $10 off** in [Digital Ocean](https://m.do.co/c/e35915938be0) or [Vultr](http://www.vultr.com/?ref=6911038) for your droplet.

Create a Droplet with Ubuntu 16.x or anything and Install WordPress with Serverpilot.

## Installing Let's Encrypt

About the script:

This script adds Let's encrypt SLL to your WordPress site created using Serverpilot and hosted on server.

ServerPilot offers auto installation of Let's encrypt with upgrade account about $10 per month. This script saves the time and works with free Serverpilot account. It's install SSL + adds a cornjob that renew Let's encrypt SSL

<code>Getting started</code>

### Clone the repo

If git isn't installed on your droplet, install it using this command

`sudo apt-get -y install git`

and then run this command to clone the repository

`sudo git clone https://github.com/nguyenrom/LetsEncrypt-Serverpilot.git && cd letsencrypt && sudo mv sple.sh /usr/local/bin/keep && sudo chmod +x /usr/local/bin/keep`

**Note**: *Let's encrypt allow only 5 SSL certificates per domain per week*. If you think you already made this mistake, you've to wait for a week before using this method or use a different domain or subdomain of the domain you're adding SSL for.

## Install SSL

Here are the simple steps to install SSL on your apps

For main domains (**Don't include www with your domain**)

Visit serverpilot > Server > App, write down the app name.

`keep install example.com app_name main`

### For sub domains

If you run your website with "www"

`keep install sub.example.com app_name sub`

## Uninstall SSL

`keep uninstall example.com app_name`

`keep uninstall sub.example.com app_name`

## Notes
Schedule auto renewal manually.

Add the following to your crontab (`crontab -e`)

**For Ubuntu 14.04**  
```
0 */12 * * * /usr/local/bin/certbot-auto renew --quiet --no-self-upgrade
```

**For Ubuntu 16.04**  
```
0 */12 * * * letsencrypt renew
```
