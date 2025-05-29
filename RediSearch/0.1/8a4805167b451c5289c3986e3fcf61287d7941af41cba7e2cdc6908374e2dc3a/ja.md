```
get_args(q::AbstractQuery) -> Vector{Union{String,Number}}
```

クエリオブジェクトに対して、RediSearchで検索する際に使用されるすべてのRedis引数をコンパイルします。

# 引数

  * `q::AbstractQuery`: クエリオブジェクト。
