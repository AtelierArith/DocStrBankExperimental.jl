```
closedendpoints(d::AI) where AI<:AbstractInterval
```

左端点/右端点が閉じているかどうかをエンコードした `Bool` のタプル。

# 例

```jldoctest
julia> closedendpoints(iv"[1,2]")
(true, true)

julia> closedendpoints(iv"(1,2]")
(false, true)

julia> closedendpoints(iv"[2,1)")
(true, false)

julia> closedendpoints(iv"(2,1)")
(false, false)
```
