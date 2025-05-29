```
UASP(client, baseport)
UASP(client, baseport, ipaddr)
```

Create UASP daemon to run on UDP ports `baseport` and `baseport+1`. If IP address is not specified, daemon only binds to localhost. The `client` must support the protocol interface methods (see `Node` for details).
