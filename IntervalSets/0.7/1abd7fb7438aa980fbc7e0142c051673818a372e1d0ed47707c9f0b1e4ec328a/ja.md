```
isclosedset(d::AbstractInterval)
```

区間は閉集合ですか？

# 例

```jldoctest
julia> isclosedset(iv"[1,2]")
true

julia> isclosedset(iv"(1,2]")
false

julia> isclosedset(iv"[1,2)")
false

julia> isclosedset(iv"(1,2)")
false
```
