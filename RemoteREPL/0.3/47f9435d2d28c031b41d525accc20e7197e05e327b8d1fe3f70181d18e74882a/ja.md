```
remote_module!(conn::Connection = _repl_client_connection, modstr::String)
```

接続 `conn` のセッション内での将来のリモートコマンドを、`modstr` で識別されるモジュールに評価されるように変更します。デフォルトの接続 `_repl_client_connection` は、最後に確立された RemoteREPL 接続です。`%module` マジックを使用するのと同等です。
