```julia
mutable struct DDE_DefaultEig{T, Tw, Tv} <: DDEBifurcationKit.AbstractDDEEigenSolver
```

Default eigen solver for DDEBifurcationKit based on the julia package NonlinearEigenproblems.jl. ore precisely, we rely on `NonlinearEigenproblems.iar_chebyshev` for the computation of eigenvalues.

## Fields

  * `maxit::Int64`: Default: 100
  * `which::Any`: Default: real
  * `σ::Any`: Default: 0.0
  * `γ::Any`: Default: 1.0
  * `tol::Any`: Default: 1.0e-10
  * `logger::Int64`: Default: 0
  * `check_error_every::Int64`: Default: 1
  * `v::Any`: Default: nothing

## Constructors

  * `DDE_DefaultEig(; kwargs...)` and `kwargs` are the fields above.
