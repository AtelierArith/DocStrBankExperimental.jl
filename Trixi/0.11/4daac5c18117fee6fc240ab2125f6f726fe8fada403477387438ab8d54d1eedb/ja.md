```
セミ離散化ハイパーボリック(mesh, equations, initial_condition, solver;
                             source_terms=nothing,
                             boundary_conditions=boundary_condition_periodic,
                             RealT=real(solver),
                             uEltype=RealT,
                             initial_cache=NamedTuple())
```

ハイパーボリックPDEのセミ離散化を構築します。
