```
rightendpoint(d::AbstractInterval)
```

区間の右端点。

# 例

```jldoctest
julia> rightendpoint(iv"[1,2]")
2

julia> rightendpoint(iv"(2,1)")
1
```
