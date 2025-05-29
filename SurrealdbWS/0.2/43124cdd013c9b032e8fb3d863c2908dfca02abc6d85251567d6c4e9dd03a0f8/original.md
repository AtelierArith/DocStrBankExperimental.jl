connect(db::Surreal, url::Union{Nothing, String}=nothing) connect to a local or remote database endpoint

# Examples

```jldoctest
julia> db = Surreal()
julia> connect(db, "ws://127.0.0.1:8000/rpc")
julia> signin(db, user="root", pass="root")
# Connect to a remote endpoint
julia> db = Surreal()
julia> connect(db,"http://cloud.surrealdb.com/rpc")
julia> signin(db, user="root", pass="root")
```
