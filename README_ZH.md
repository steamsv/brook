# Brook

[ð¬ð§ English](README.md)

[![Build Status](https://travis-ci.org/txthinking/brook.svg?branch=master)](https://travis-ci.org/txthinking/brook)
[![å¼æºåè®®: GPL v3](https://img.shields.io/badge/%E5%BC%80%E6%BA%90%E5%8D%8F%E8%AE%AE-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
[![æèµ ](https://img.shields.io/badge/%E6%94%AF%E6%8C%81-%E6%8D%90%E8%B5%A0-ff69b4.svg)](https://github.com/sponsors/txthinking)

| ð | ð |
| --- | --- |
| å¿è¯» | https://txthinking.github.io/brook/#/zh-cn/README |
| å®è£ CLI | https://txthinking.github.io/brook/#/zh-cn/install-cli |
| å®è£ GUI (macOS, Windows, iOS, Android, OpenWrt) | https://txthinking.github.io/brook/#/zh-cn/install-gui-client |
| OpenWrt CLI | https://txthinking.github.io/brook/#/zh-cn/brook-tproxy |
| ð¹ | âï¸ |
| Blog | https://talks.txthinking.com |
| Youtube | https://www.youtube.com/txthinking |
| è®ºå | https://github.com/txthinking/brook/discussions |
| Telegram é¢é | https://t.me/brookchannel |

---

## ä»ä¹æ¯ Brook

Brook æ¯ä¸ä¸ªè·¨å¹³å°çå¼ºå å¯æ ç¹å¾çä»£çè½¯ä»¶. åç± KISS å²å­¦.

â¤ï¸ A project by [txthinking.com](https://www.txthinking.com)

### å®è£ CLI (å½ä»¤è¡çæ¬)

```
curl -L https://github.com/txthinking/brook/releases/latest/download/brook_linux_amd64 -o /usr/bin/brook
chmod +x /usr/bin/brook
```

### ä½ä¸ºsystemæå¡`/lib/systemd/system/brook.service`
```
[Unit]
Description=brook service
After=network.target syslog.target
Wants=network.target

[Service]
Type=simple
ExecStart=/usr/bin/brook socks5 --socks5 0.0.0.0:8443
[Install]
WantedBy=multi-user.target
```
- çæ

```
systemctl daemon-reload
systemctl restart brook
systemctl enable brook
```
### [æ¨è] éè¿ [nami](https://github.com/txthinking/nami) å®è£ CLI, å¹¶éè¿ [joker](https://github.com/txthinking/joker) è¿è¡ `brook wswserver`

> ð åªéå¤å¶è¿åè¡å½ä»¤ç²è´´å³å¯, ä½ å¯ä»¥ç§°æ­¤ä¸º**ðä¸é®èæ¬ð**

```
curl -L https://git.io/getnami | bash && sleep 3 && exec -l $SHELL
nami install github.com/txthinking/joker
nami install github.com/txthinking/brook
joker brook wsserver --listen :9999 --password hello
```

> ç¶å, ä½ ç `brook wsserver` æ¯ `ws://YOUR_SERVER_IP:9999`, å¯ç æ¯ `password`

[æ¥çææ¡£](https://txthinking.github.io/brook/#/zh-cn/install-cli)

### å®è£ GUI (å¾å½¢å®¢æ·ç«¯)

[æ¥çææ¡£](https://txthinking.github.io/brook/#/zh-cn/install-gui-client)

## ä½¿ç¨

```
NAME:
   Brook - A cross-platform strong encryption and not detectable proxy

USAGE:
   brook [global options] command [command options] [arguments...]

VERSION:
   20210701

AUTHOR:
   Cloud <cloud@txthinking.com>

COMMANDS:
   server          Run as brook server, both TCP and UDP
   client          Run as brook client, both TCP and UDP, to start a socks5 proxy, [src <-> socks5 <-> brook client <-> brook server <-> dst]
   wsserver        Run as brook wsserver, both TCP and UDP, it will start a standard http server and websocket server
   wsclient        Run as brook wsclient, both TCP and UDP, to start a socks5 proxy, [src <-> socks5 <-> brook wsclient <-> brook wsserver <-> dst]
   wssserver       Run as brook wssserver, both TCP and UDP, it will start a standard https server and websocket server
   wssclient       Run as brook wssclient, both TCP and UDP, to start a socks5 proxy, [src <-> socks5 <-> brook wssclient <-> brook wssserver <-> dst]
   relayoverbrook  Run as relay over brook, both TCP and UDP, this means access [from address] is equal to [to address], [src <-> from address <-> brook server/wsserver/wssserver <-> to address]
   dns             Run as dns server over brook, both TCP and UDP, [src <-> brook dns <-> brook server/wsserver/wssserver <-> dns] or [src <-> brook dns <-> dnsForBypass]
   tproxy          Run as transparent proxy, both TCP and UDP, only works on Linux, [src <-> brook tproxy <-> brook server/wsserver/wssserver <-> dst]
   link            Print brook link
   qr              Print brook server QR code
   connect         Connect via standard sharing link (brook server & brook wsserver & brook wssserver)
   relay           Run as standalone relay, both TCP and UDP, this means access [from address] is equal to access [to address], [src <-> from address <-> to address]
   socks5          Run as standalone standard socks5 server, both TCP and UDP
   socks5tohttp    Convert socks5 to http proxy, [src <-> listen address(http proxy) <-> socks5 address <-> dst]
   hijackhttps     Hijack domains and assume is TCP/TLS/443. Requesting these domains from anywhere in the system will be hijacked . [src <-> brook hijackhttps <-> socks5 server] or [src <-> direct]
   pac             Run as PAC server or save PAC to file
   servers         Run as multiple brook servers
   relays          Run as multiple standalone relays
   map             Run as mapping, both TCP and UDP, this means access [from address] is equal to [to address], [src <-> from address <-> brook <-> to address]
   howto           Print some useful tutorial resources
   help, h         Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --debug, -d               Enable debug (default: false)
   --listen value, -l value  Listen address for debug (default: ":6060")
   --help, -h                show help (default: false)
   --version, -v             print the version (default: false)

COPYRIGHT:
   https://github.com/txthinking/brook
```

[ææ¡£](https://txthinking.github.io/brook/#/zh-cn/)

## è´¡ç®

è¯·åéè¯» [CONTRIBUTING.md](https://github.com/txthinking/brook/blob/master/.github/CONTRIBUTING.md)

## å¼æºåè®®

åºäº GPLv3 åè®®å¼æº
