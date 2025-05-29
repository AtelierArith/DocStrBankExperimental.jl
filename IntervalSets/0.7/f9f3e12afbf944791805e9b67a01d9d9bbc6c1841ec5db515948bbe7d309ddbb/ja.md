```
isleftopen(d::AbstractInterval)
```

区間の左端点が開いていますか？

# 例

```jldoctest
julia> isleftopen(iv"[1,2]")
false

julia> isleftopen(iv"(2,1)")
true
```
