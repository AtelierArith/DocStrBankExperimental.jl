```
get_token()
```

トークンリクエストのためのIdealista Search APIの解析されたレスポンスを返します

# 注意事項

APIKEYとSECRETは環境変数として定義する必要があります。生成されたトークンはtempdirにキャッシュされ、期限切れの日付前にget_token関数への新しい呼び出しはキャッシュされた値を返します。

# 例

```julia
julia>get_token()
[ Info: Getting new access token
Dict{String, Any} with 5 entries:
  "access_token" => "token_value"
  "token_type"   => "bearer"
  "scope"        => "read"
  "expires_in"   => DateTime("2022-08-14T03:07:24.573")
  "jti"          => "jti_value"

```
