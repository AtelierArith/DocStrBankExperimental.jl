```
leftendpoint(d::AbstractInterval)
```

区間の左端点。

# 例

```jldoctest
julia> leftendpoint(iv"[1,2]")
1

julia> leftendpoint(iv"(2,1)")
2
```
