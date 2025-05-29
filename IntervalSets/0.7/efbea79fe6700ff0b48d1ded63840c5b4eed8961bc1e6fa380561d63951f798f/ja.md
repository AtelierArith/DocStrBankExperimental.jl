```
isrightclosed(d::AbstractInterval)
```

区間は右端点で閉じていますか？

# 例

```jldoctest
julia> isrightclosed(iv"[1,2]")
true

julia> isrightclosed(iv"(2,1)")
false
```
