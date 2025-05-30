```
mutable struct Role <:AbstractRole
```

# 権限の付与

```julia
grant!(role, permissions::Permission...)
grant!(role, roles::Role...)
```

# 権限と役割の削除

```julia
revoke!(role, permissions::Permission...)

revoke!(role, roles::Role...)
```
