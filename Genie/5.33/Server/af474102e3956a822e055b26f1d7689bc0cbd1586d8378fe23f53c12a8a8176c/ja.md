```
down(; webserver::Bool = true, websockets::Bool = true) :: ServersCollection
```

サーバーをシャットダウンし、`webserver` と `websockets` のどちらのサーバーを停止するかをオプションで指定します。サーバーは `SERVERS` コレクションから削除されません。コレクションを返します。
