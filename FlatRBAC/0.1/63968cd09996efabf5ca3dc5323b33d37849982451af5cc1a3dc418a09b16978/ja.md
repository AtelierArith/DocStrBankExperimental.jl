```
mutable struct Role <:AbstractRole
```

# 権限の付与

```julia
grant!(role, permissions::Permission...)
grant!(role, roles::Role...)
```

# 権限とロールの削除

```julia
revoke!(role, permissions::Permission...)

revoke!(role, roles::Role...)
```
