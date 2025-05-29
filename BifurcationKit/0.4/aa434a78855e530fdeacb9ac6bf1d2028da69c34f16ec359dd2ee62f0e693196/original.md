```julia
mutable struct GMRESKrylovKit{T, Tl} <: BifurcationKit.AbstractIterativeLinearSolver
```

Create a linear solver based on `linsolve` from `KrylovKit.jl`. Can be used to solve `(a₀ * I + a₁ * J) * x = rhs`.

## Fields

  * `dim::Int64`: Krylov Dimension Default: KrylovDefaults.krylovdim[]
  * `atol::Any`: Absolute tolerance for solver Default: KrylovDefaults.tol[]
  * `rtol::Any`: Relative tolerance for solver Default: KrylovDefaults.tol[]
  * `maxiter::Int64`: Maximum number of iterations Default: KrylovDefaults.maxiter[]
  * `verbose::Int64`: Verbosity ∈ {0,1,2} Default: 0
  * `issymmetric::Bool`: If the linear map is symmetric, only meaningful if T<:Real Default: false
  * `ishermitian::Bool`: If the linear map is hermitian Default: false
  * `isposdef::Bool`: If the linear map is positive definite Default: false
  * `Pl::Any`: Left preconditioner Default: nothing

!!! tip "Different linear solvers"
    By tuning the options, you can select CG, GMRES... see [here](https://jutho.github.io/KrylovKit.jl/stable/man/linear/#KrylovKit.linsolve)

