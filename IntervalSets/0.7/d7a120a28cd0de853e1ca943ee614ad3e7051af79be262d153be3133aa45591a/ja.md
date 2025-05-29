```
isrightopen(d::AbstractInterval)
```

区間は右端点で開いていますか？

# 例

```jldoctest
julia> isrightopen(iv"[1,2]")
false

julia> isrightopen(iv"(2,1)")
true
```
