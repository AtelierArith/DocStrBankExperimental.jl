```
UASP2(client, port)
UASP2(client, port, ipaddr)
```

Create UASP v2 daemon to run on TCP `port`. If IP address is not specified, daemon only binds to localhost. The `client` must support the protocol interface methods (see `Node` for details).
