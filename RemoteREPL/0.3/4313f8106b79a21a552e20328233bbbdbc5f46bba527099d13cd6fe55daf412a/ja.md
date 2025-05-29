```
serve_repl([address=Sockets.localhost,] port=27754; [on_client_connect=nothing])
serve_repl(server)
```

インターフェース `address` と `port` でリッスンする REPL サーバーを起動します。通常の操作では `serve_repl()` は REPL クライアントに無限にサービスを提供するため（つまり、戻りません）、他の有用な作業を同時に行うために `@async serve_repl()` を使用して起動することを一般的にお勧めします。

フック `on_client_connect` を提供することで、各クライアントが接続した後に `ServerSideSession` を変更することができます。これを使用して、クライアントがコマンドを評価するデフォルトモジュールを定義できます。

サーバーを停止できるようにするには、すでにリッスンしている `server` オブジェクト（`Sockets.listen()` の結果）を渡すことができます。サーバーは、必要に応じて `close(server)` を使用して別のタスクからキャンセルできます。

## セキュリティ

`serve_repl()` は *認証されていない、暗号化されていないプロトコル* を使用しているため、他のユーザーが信頼できないオープンネットワークやマルチユーザーのマシンでは使用しないでください。オープンネットワークの場合は、デフォルトの `address=Sockets.localhost` と、クライアント側の `connect_repl()` によって提供される自動 ssh トンネルサポートを使用してください。
