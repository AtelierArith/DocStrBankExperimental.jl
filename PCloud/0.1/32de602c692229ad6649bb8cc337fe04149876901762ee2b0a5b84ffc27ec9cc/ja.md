```
oauth2_token(client::PCloudClient; kwargs...)
```

このメソッドは、アプリがコードフローを使用しているときに使用されます。アプリは、このメソッドを呼び出して、ユーザーがアプリを承認した後にベアラートークンを取得します。

このメソッドは、アプリの `key` と `secret` を期待します。

また、oauth2_tokenからのリダイレクトで受け取った `code` が必要です。

出典: https://docs.pcloud.com/methods/oauth*2.0/oauth2*token.html

# 引数

  * `client_id::String`: - アプリケーションのID
  * `client_secret::String`: - アプリケーションの秘密コード
  * `code::code`: - 認可ページからのリダイレクトに返されたコード

# 出力

`code` が検証されると、メソッドは次のフィールドを持つオブジェクトを返します:

  * `access_token::String`: pCloud APIメソッドを呼び出すために使用できるトークン。
  * `token_type::String`: トークンのタイプ（常にベアラー）。
  * `uid::Int`: アプリへのアクセスを許可したユーザーのID。

# 出力例

```
{
    result: 0,
    access_token: "dghdghdj",
    token_type: "bearer",
    uid: 34535
}
```
