```
connect_gsheet(client_id::String, client_secret::String; redirect_uri::String = "http://localhost:8081")
```

Google Sheets APIに接続し、OAuth 2.0認証フローを使用してアクセストークンを取得します。資格情報を取得するには、Google Cloud Console -> APIs and Services -> Credentials -> Create Credentials -> Create OAuth Client ID -> Desktop Appに移動します。これには`client_id`と`client_secret`が含まれます。

# 引数

  * `client_id::String`: Google Cloud Consoleから取得したクライアントID。
  * `client_secret::String`: Google Cloud Consoleから取得したクライアントシークレット。
  * `redirect_uri::String`: 認証サーバーがアクセスを許可した後にユーザーをリダイレクトするURI。デフォルトは"http://localhost:8081"です。

# 戻り値

  * クライアントID、クライアントシークレット、リダイレクトURI、およびアクセストークンを含む`GSheetAuth`のインスタンス。

# 例

```julia
julia> connect_gsheet("your_client_id", "your_client_secret")
```
