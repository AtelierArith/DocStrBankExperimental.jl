```
start!(server::Server) -> Nothing
```

MCPサーバーを起動し、ログを設定してメインサーバーループに入ります。

# 引数

  * `server::Server`: 起動するサーバーインスタンス

# 戻り値

  * `Nothing`: サーバーが停止した後に関数が戻ります

# 例外

  * `ServerError`: サーバーがすでに実行中の場合
