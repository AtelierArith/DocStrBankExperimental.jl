```
isleftclosed(d::AbstractInterval)
```

区間は左端点で閉じていますか？

# 例

```jldoctest
julia> isleftclosed(iv"[1,2]")
true

julia> isleftclosed(iv"(2,1)")
false
```
