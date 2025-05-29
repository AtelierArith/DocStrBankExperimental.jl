```
remote_module!(conn::Connection = _repl_client_connection, mod::Module)
```

接続 `conn` のセッション内での将来のリモートコマンドをモジュール `mod` に評価されるように変更します。デフォルトの接続 `_repl_client_connection` は、最後に確立された RemoteREPL 接続です。モジュールがローカルで評価できない場合は、名前を文字列として渡します。これは `%module` マジックを使用するのと同等です。
