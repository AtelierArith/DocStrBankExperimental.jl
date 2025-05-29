```
PrefectAPI(url::String, key::SecretString) <:AbstractPrefectInterface
PrefectAPI(url::String)
PrefectAPI()
```

Mutable structはPrefectサーバーのAPIエンドポイントを格納します。すべての`PrefectInterface`操作は、ブロック情報を取得するために実行中のPrefectサーバーに接続することに依存しています。引数なしのコンストラクタは環境変数`PREFECT_API_URL`、`PREFECT_API_KEY`を割り当てます。

`PREFECT_API_KEY`が存在しない場合、空の文字列が`key`に割り当てられます。認証のないPrefectサーバー（または接続文字列によって管理される認証）では、空のキーはAPI呼び出しに干渉しません。

# 例:

```jldoctest
julia> using PrefectInterfaces

julia> ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api"; ENV["PREFECT_API_KEY"] = "zyxw4321";

julia> api = PrefectAPI()
PrefectAPI("http://127.0.0.1:4300/api", ####Secret####)

julia> api.url
"http://127.0.0.1:4300/api"

julia> api.key.secret
"zyxw4321"

julia> api.url = "https://api.prefect.cloud/api/accounts/0eEXAMPLE";

julia> api.key = SecretString("abcd1234")
####Secret####

julia> api = PrefectAPI("https://api.prefect.cloud/api/accounts/0eEXAMPLE", "abcd1234")
PrefectAPI("https://api.prefect.cloud/api/accounts/0eEXAMPLE", ####Secret####)
```
