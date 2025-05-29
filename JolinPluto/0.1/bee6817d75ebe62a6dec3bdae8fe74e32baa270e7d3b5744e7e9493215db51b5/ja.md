```
authenticate_token()
authenticate_token("exampleaudience")
```

一般的なクラウドプロバイダーでの認証に使用できるJSON Web Tokenを作成します。

cloud.jolin.ioでは、トークンはcloud.jolin.ioによって発行および署名され、Github Actions（自動テストに使用）では、対応するgithubトークンが返されます。
