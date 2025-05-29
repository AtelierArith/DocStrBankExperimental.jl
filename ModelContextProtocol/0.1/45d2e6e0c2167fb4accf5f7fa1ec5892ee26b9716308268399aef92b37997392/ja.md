```
subscribe!(server::Server, uri::String, callback::Function) -> Server
```

URIで識別される特定のリソースの更新にサブスクライブします。

# 引数

  * `server::Server`: サーバーインスタンス
  * `uri::String`: サブスクライブするリソースのURI
  * `callback::Function`: リソースが更新されたときに呼び出される関数

# 戻り値

  * `Server`: メソッドチェイニングのためのサーバーインスタンス
