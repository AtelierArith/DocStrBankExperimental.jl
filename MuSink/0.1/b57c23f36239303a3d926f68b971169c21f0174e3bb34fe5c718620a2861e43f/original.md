```
Barycenter(targets; kwargs...)
```

Directly create a workspace that puts `targets` in a star-shaped cost tree around a barycenter-node with `rho = 0`. Valid keyword arguments are the ones for [`Problem`](@ref) (except for `root`) and [`Workspace`](@ref).
