```
stop!(server::Server) -> Nothing
```

実行中のMCPサーバーを停止します。

# 引数

  * `server::Server`: 停止するサーバーインスタンス

# 戻り値

  * `Nothing`: サーバーを非アクティブに設定した後に関数が返します

# 例外

  * `ServerError`: サーバーが現在実行中でない場合
