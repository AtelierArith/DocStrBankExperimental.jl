```
SemidiscretizationHyperbolicParabolic(mesh, both_equations, initial_condition, solver;
                                      solver_parabolic=default_parabolic_solver(),
                                      source_terms=nothing,
                                      both_boundary_conditions=(boundary_condition_periodic, boundary_condition_periodic),
                                      RealT=real(solver),
                                      uEltype=RealT,
                                      both_initial_caches=(NamedTuple(), NamedTuple()))
```

ハイパーボリック-パラボリックPDEの半離散化を構築します。
