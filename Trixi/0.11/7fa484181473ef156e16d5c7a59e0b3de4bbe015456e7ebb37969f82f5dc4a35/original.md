```
adapt_to_mesh_level(u_ode, semi, level)
adapt_to_mesh_level(sol::Trixi.TrixiODESolution, level)
```

Use the regular adaptive mesh refinement routines to adaptively refine/coarsen the solution `u_ode` with semidiscretization `semi` towards a uniformly refined grid with refinement level `level`. The solution and semidiscretization are copied such that the original objects remain *unaltered*.

A convenience method accepts an ODE solution object, from which solution and semidiscretization are extracted as needed.

See also: [`adapt_to_mesh_level!`](@ref)
