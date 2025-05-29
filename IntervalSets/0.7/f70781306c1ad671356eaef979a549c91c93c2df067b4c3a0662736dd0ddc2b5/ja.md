```
endpoints(d::AI) where AI<:AbstractInterval
```

区間の左端点と右端点を含むタプル。

# 例

```jldoctest
julia> endpoints(iv"[1,2]")
(1, 2)

julia> endpoints(iv"(2,1)")
(2, 1)
```
