realdb*post(url, body = "{"name": "real*db_test"}"; query = Dict())

エンドポイントへのPOSTリクエスト。

# 例

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
# realdb_post("/message_list")
body =Dict("user_id" => "jack", "text" => "Ahoy!")
realdb_post("/message_list",body)
```

## 注意事項:

Realtime DatabaseのREST APIドキュメントによると、POSTはクライアントSDKを使用する際の「プッシュ」操作に相当します。このプッシュ操作は常にランダムIDの下にデータを追加することを伴います。プッシュの場合、それを避けることはできません。

データを追加したいノードの名前がわかっている場合は、代わりにPUTを使用するべきです。これはクライアントSDKを使用する際の「set」操作に相当します。
