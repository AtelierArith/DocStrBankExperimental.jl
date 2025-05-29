```
KdbConnectionInfo(host::String, port::Integer[, user::String, timeout::Integer])
```

Information for a KDB connection. Requires `host` and `port`. `user and`timeout`are optional.`timeout` is an integer representing milliseconds until query timeout.

Open a connection with `open(conn::KdbConnectionInfo)`
