```
has_permission(perms::Integer, perm::Permission) -> Bool
```

Determine whether a bitwise OR of permissions contains one [`Permission`](@ref).

## Examples

```jldoctest; setup=:(using Ekztazy)
julia> has_permission(0x0420, PERM_VIEW_CHANNEL)
true

julia> has_permission(0x0420, PERM_ADMINISTRATOR)
false

julia> has_permission(0x0008, PERM_MANAGE_ROLES)
true
```
