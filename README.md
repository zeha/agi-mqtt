agi-mqtt
========

Asterisk to MQTT Bridge

Installation
============

Clone repository somewhere convenient, possibly /etc/asterisk/agi.

Copy mqtt.cfg.sample to mqtt.cfg and edit the values. username/password are optional.


Integration
===========

Asterisk
--------

extensions.conf snippet:

```
exten => 43123456789,1,AGI(/etc/asterisk/agi/mqtt,/etc/asterisk/agi/mqtt.cfg,calls/${ARG1})
```

Or, if you need to override the extension, for example in a macro, use this:

```
[macro-mqtt]
exten => s,1,AGI(/etc/asterisk/agi/mqtt,/etc/asterisk/agi/mqtt.cfg,calls/${ARG1},${ARG2})
```

mqttwarn
--------

(See https://github.com/jpmens/mqttwarn for info about mqttwarn.)

Example config snippet:
```
[calls/missed]
targets = log:info, xmpp:ch
format = From {callerid} ({calleridname}) at {_dthhmm} for {extension}
title = Missed call
```

