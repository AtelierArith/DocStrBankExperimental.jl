```
Semidiscretization(mesh, equations, initial_condition, solver;
                   source_terms=nothing,
                   boundary_conditions=boundary_condition_periodic,
                   RealT=real(solver),
                   uEltype=RealT,
                   initial_cache = (tmp1 = Array{RealT}(undef, nnodes(mesh)),
                                    tmp_partitioned = allocate_coefficients(mesh, equations, solver)))
```

Construct a semidiscretization of a PDE.
