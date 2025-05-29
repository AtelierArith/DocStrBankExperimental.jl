```
WaveEquationNonperiodicSemidiscretization(D, left_bc, right_bc)
```

A semidiscretization of the linear wave equation     $\partial_t^2 u(t,x) = \partial_x^2 u(t,x)$.

`D` is assumed to be a second-derivative SBP operator and the boundary conditions can be `Val(:HomogeneousNeumann)`, `Val(:HomogeneousDirichlet)`, or `Val(:NonReflecting)`.
