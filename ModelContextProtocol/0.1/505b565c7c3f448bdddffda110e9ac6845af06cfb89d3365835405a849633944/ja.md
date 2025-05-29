```
unsubscribe!(server::Server, uri::String, callback::Function) -> Server
```

特定のリソースURIとコールバック関数の購読を解除します。

# 引数

  * `server::Server`: サーバーインスタンス
  * `uri::String`: 購読解除するリソースURI
  * `callback::Function`: 削除するコールバック関数

# 戻り値

  * `Server`: メソッドチェイニング用のサーバーインスタンス
