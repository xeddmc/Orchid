# Orchid

Java based TOR client without the TOR browser bundle and with a SOCKS5 proxy.

Compatible with Eclipse.

## Running Orchid

To start the Orchid SOCKS5 proxy, perform the following:

`java -jar orchid-version.jar`  
Orchid will first attempt to establish a connection to the Tor network and gather directory information. Once it has enough directory information it will begin building circuits.

## Using Orchid to browse the Tor network

To test Orchid, you can tell your browser to use Orchid as a proxy (Using something like FoxyProxy or ProxyOmega allows the use of wildcards (`.*.`) which make accessing .onion sites easier). 

**Please Note:** _Orchid + your browser alone isn't a secure replacement for the_ [_Tor Browser bundle_](https://www.torproject.org/download/)_, which has many other enhancements beyond Tor itself._

Example: By default DNS lookups are not sent over a configured SOCKS5 proxy in Firefox. You can change this potentially de-anonymizing default configuration by going to the URL `about:config` and setting the property `network.proxy.socks_remote_dns` to `true` (this is already done in the Tor Browser).

## Using the dashboard

Orchid includes a info status/dashboard option to observe the internal state of Tor. To start this, set the following property when the JAR is run:

```
java -Dcom.subgraph.orchid.dashboard.port=10000 orchid-version.jar
```

To access the dashboard, just connect to the port (10000) with netcat. (netcat is usually installed by default in Linux. It can be used with `netcat [options] host port` check out `netcat help` or `man netcat` for more info on that specific tool.

## Using Orchid as a library

The Orchid Tor client exposes a SocketFactory that can be used within a JVM application.
