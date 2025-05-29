set(db::Surreal; params)::Nothing   このメソッドは、現在の接続のための名前空間とデータベースを指定します

```jldoctest
julia> let(db,params=("website", "https://surrealdb.com/"))
```
