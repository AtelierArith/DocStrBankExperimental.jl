```
remotecmd(conn::Connection, out_stream::IO, cmdstr::String)
```

Evaluate `cmdstr` in the remote session of connection `conn` and write result into `out_stream`. Also supports the magic `RemoteREPL` commands like `%module` and `%include`.
