# How to use Onion Omega as a print server

## Sources - read first
 * https://onion.io/2bt-omega-print-server/
 * https://openwrt.org/docs/guide-user/services/print_server/p910ndprinterserver

## p910nd installation
The default onion Omega distribution feeds don't contain the ``p910nd`` package. To install the p910nd, I needed to:
 * ``vim /etc/opkg/distfeeds.conf`` - uncomment the OpenWRT dist feeds
 * ``opkg update``
 * ``opkg install p910nd``
 * ``vim /etc/config/p910nd``
  ````
  config p910nd
        option device        /dev/usb/lp0
        option port          0
        option bidirectional 1
        option enabled       1
  ````
  * ``/etc/init.d/p910nd restart``
## Useful commands
 * ``opkg update``
 * ``opkg list-installed``
 * ``opkg list | grep p910nd``

## What else
I'm using IP for the printer port configuration (not sure if computername would work too). So I configured the home router's DHCP to always assign the same IP for the Onion Omega's MAC address (Static IP assignment, pre-assigned DHCP IP Addresses)

## Pitfalls
Onion Omega firmware upgrade silently uninstalled the p910nd package. I needed to reinstall it. The configuration was not removed by the upgrade.

## Setup details
* [Onion Omega2+](https://onion.io/omega2/)
* [Mini Dock](https://onion.io/store/mini-dock/)
* HP LaserJet P2015
