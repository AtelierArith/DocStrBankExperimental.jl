```julia
struct COPBLS{dim, 𝒯, TL, TU, Tp, Ts, Tj} <: BifurcationKit.AbstractBorderedLinearSolver
```

Bordered linear solver based on the condensation of parameters. `dim` in the struct definition is the size of the border counting the phase condition. It is thus `dim = 1` for COPLS and `dim = 2` for the case of arclength continuation of periodic orbits as there are two constraints: the phase and the arclength.

## Fields

  * `cache::BifurcationKit.COPCACHE`: Cache for the COP method. It is a subtype of COPCACHE.
  * `solver::Any`: Linear solver. Defaults to `nothing`.
  * `J::Any`: Cache for the bordered jacobian matrix.

## Constructors

  * `COPBLS()`
  * `COPBLS(coll::PeriodicOrbitOCollProblem; N = 0, cache::COPCACHE, solver = nothing, J = nothing)`

## Related

See `solve_cop`.
