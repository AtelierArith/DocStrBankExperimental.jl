```
isopenset(d::AbstractInterval)
```

区間は開集合ですか？

# 例

```jldoctest
julia> isopenset(iv"[1,2]")
false

julia> isopenset(iv"(1,2]")
false

julia> isopenset(iv"[1,2)")
false

julia> isopenset(iv"(1,2)")
true
```
