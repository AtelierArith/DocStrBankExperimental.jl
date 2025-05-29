```
remote_module!(conn::Connection = _repl_client_connection, mod::Module)
```

Change future remote commands in the session of connection `conn` to be evaluated into module `mod`. The default connection `_repl_client_connection` is the last established RemoteREPL connection. If the module cannot be evaluated locally pass the name as a string. Equivalent to using the `%module` magic.
