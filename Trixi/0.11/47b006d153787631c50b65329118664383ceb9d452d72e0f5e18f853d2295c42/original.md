```
adapt_to_mesh_level!(u_ode, semi, level)
adapt_to_mesh_level!(sol::Trixi.TrixiODESolution, level)
```

Like [`adapt_to_mesh_level`](@ref), but modifies the solution and parts of the semidiscretization (mesh and caches) in place.
