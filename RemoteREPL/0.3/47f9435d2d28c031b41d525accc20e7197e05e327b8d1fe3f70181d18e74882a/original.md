```
remote_module!(conn::Connection = _repl_client_connection, modstr::String)
```

Change future remote commands in the session of connection `conn` to be evaluated into module identified by `modstr`. The default connection `_repl_client_connection` is the last established RemoteREPL connection. Equivalent to using the `%module` magic.
