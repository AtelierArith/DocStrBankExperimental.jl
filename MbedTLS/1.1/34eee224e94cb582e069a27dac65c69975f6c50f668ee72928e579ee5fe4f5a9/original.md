```
SSLConfig(verify::Bool; log_secrets=nothing)
```

Initialise a client SSLConfig for connecting to a server.

If `verify` is false, do not check that certificates are valid.

If `log_secrets` is a string, save connection secrets to a file with that name. This is useful for decrypting traffic captured with Wireshark when debugging.
