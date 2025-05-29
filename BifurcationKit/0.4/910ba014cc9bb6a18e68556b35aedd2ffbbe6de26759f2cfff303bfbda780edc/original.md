```julia
struct COPLS{dim, 𝒯, TL, TU, Tp} <: BifurcationKit.AbstractDirectLinearSolver
```

Linear solver based on the condensation of parameters.

## Fields

  * `cache::BifurcationKit.COPCACHE`

## Constructors

  * `COPBLS()`
  * `COPBLS(coll::PeriodicOrbitOCollProblem; cache::COPCACHE, solver = nothing, J = nothing)`

## Related

See `solve_cop`.
