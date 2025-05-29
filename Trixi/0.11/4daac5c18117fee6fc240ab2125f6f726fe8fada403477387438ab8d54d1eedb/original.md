```
SemidiscretizationHyperbolic(mesh, equations, initial_condition, solver;
                             source_terms=nothing,
                             boundary_conditions=boundary_condition_periodic,
                             RealT=real(solver),
                             uEltype=RealT,
                             initial_cache=NamedTuple())
```

Construct a semidiscretization of a hyperbolic PDE.
