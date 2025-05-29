```
has_permission(perms::Integer, perm::Permission) -> Bool
```

ビット単位のOR演算によって権限が一つの [`Permission`](@ref) を含むかどうかを判断します。

## 例

```jldoctest; setup=:(using Ekztazy)
julia> has_permission(0x0420, PERM_VIEW_CHANNEL)
true

julia> has_permission(0x0420, PERM_ADMINISTRATOR)
false

julia> has_permission(0x0008, PERM_MANAGE_ROLES)
true
```
