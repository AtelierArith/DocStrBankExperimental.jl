```
remotecmd(conn::Connection, out_stream::IO, cmdstr::String)
```

接続 `conn` のリモートセッションで `cmdstr` を評価し、結果を `out_stream` に書き込みます。また、`%module` や `%include` のようなマジック `RemoteREPL` コマンドもサポートしています。
