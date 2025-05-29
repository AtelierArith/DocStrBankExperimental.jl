realdb*delete(url, body = Dict("name"=> "real*db_test"); query = Dict())

`DELETE` リクエストをエンドポイントに送信

# 例

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
realdb_delete("/users/jack/name/last")
```
