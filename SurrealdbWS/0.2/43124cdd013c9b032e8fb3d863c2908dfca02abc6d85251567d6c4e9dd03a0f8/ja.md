connect(db::Surreal, url::Union{Nothing, String}=nothing) は、ローカルまたはリモートのデータベースエンドポイントに接続します。

# 例

```jldoctest
julia> db = Surreal()
julia> connect(db, "ws://127.0.0.1:8000/rpc")
julia> signin(db, user="root", pass="root")
# リモートエンドポイントに接続
julia> db = Surreal()
julia> connect(db,"http://cloud.surrealdb.com/rpc")
julia> signin(db, user="root", pass="root")
```
