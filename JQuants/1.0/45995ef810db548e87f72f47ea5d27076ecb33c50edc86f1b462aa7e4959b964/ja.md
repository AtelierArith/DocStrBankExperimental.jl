```
authorize(refresh_token::AbstractString)
authorize(emailaddress::AbstractString, password::AbstractString)
```

リフレッシュトークン `refresh_token`、またはメールアドレス `emailaddress` とパスワード `password` の組み合わせで認証します。認証後は `true` を返します。

このAPIの詳細は[こちら](https://jpx.gitbook.io/j-quants-api-en/api-reference/refreshtoken)と[こちら](https://jpx.gitbook.io/j-quants-api-en/api-reference/refresh)です。

このパッケージは、一時的にあなたのIDトークンとリフレッシュトークンをパッケージ内部の変数として保持します。認証が完了すると、Juliaのプロセスが終了するか、トークンが期限切れになるまで再認証は必要ありません。トークンは `JQuants.check_refresh_token()` と `JQuants.check_id_token()` を使用して確認できます。

# 例

```jldoctest
julia> reftoken = [YOUR REFRESH TOKEN];

julia> authorize(reftoken)
true
```

```jldoctest
julia> email, pass = [YOUR EMAIL ADDRESS], [YOUR PASSWORD]

julia> authorize(email, pass)
true
```
