realdb_get(url; query = Dict())

エンドポイントへのGETリクエスト。

# 例

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
realdb_get("/users/jack/name")
```
