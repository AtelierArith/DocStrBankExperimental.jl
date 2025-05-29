```julia
mutable struct GMRESIterativeSolvers{T, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

Linear solver based on `gmres` from `IterativeSolvers.jl`. Can be used to solve `(a₀ * I + a₁ * J) * x = rhs`.

## Fields

  * `abstol::Any`: Absolute tolerance for solver Default: 0.0
  * `reltol::Any`: Relative tolerance for solver Default: 1.0e-8
  * `restart::Int64`: Number of restarts Default: 200
  * `maxiter::Int64`: Maximum number of iterations Default: 100
  * `N::Int64`: Dimension of the problem Default: 0
  * `verbose::Bool`: Display information during iterations Default: false
  * `log::Bool`: Record information Default: true
  * `initially_zero::Bool`: Start with zero guess Default: true
  * `Pl::Any`: Left preconditioner Default: IterativeSolvers.Identity()
  * `Pr::Any`: Right preconditioner Default: IterativeSolvers.Identity()
  * `ismutating::Bool`: Whether the linear operator is written inplace Default: false
