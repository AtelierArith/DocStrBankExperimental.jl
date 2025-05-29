```
JUA_ServerConfig_setMinimal(config, portNumber[, certificate])
```

creates a new server config with one endpoint. The config will set the tcp network layer to the given port and adds a single endpoint with the security policy $SecurityPolicy#None$ to the server. A server certificate may be supplied but is optional.
