```
mutable struct Role <:AbstractRole
```

# Grating permissions

```julia
grant!(role, permissions::Permission...)
grant!(role, roles::Role...)
```

# Removing permissions and roles

```julia
revoke!(role, permissions::Permission...)

revoke!(role, roles::Role...)
```
