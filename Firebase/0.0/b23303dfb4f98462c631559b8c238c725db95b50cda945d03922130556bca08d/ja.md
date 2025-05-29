realdb*patch(url, body = Dict("name"=> "real*db_test"); query = Dict())

`PATCH` リクエストをエンドポイントに送信します。

# 例

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
body =Dict("last"=>"Jones")
realdb_patch("/users/jack/name/",body)
```
