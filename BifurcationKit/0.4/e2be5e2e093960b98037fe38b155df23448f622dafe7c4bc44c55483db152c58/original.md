```julia
struct EigKrylovKit{T, vectype} <: BifurcationKit.AbstractMFEigenSolver
```

Create an eigen solver based on `KrylovKit.jl`.

## Fields

  * `dim::Int64`: Krylov Dimension Default: KrylovDefaults.krylovdim[]
  * `tol::Any`: Tolerance Default: 0.0001
  * `restart::Int64`: Number of restarts Default: 200
  * `maxiter::Int64`: Maximum number of iterations Default: KrylovDefaults.maxiter[]
  * `verbose::Int64`: Verbosity ∈ {0, 1, 2} Default: 0
  * `which::Symbol`: Which eigenvalues are looked for :LR (largest real), :LM, ... Default: :LR
  * `issymmetric::Bool`: If the linear map is symmetric, only meaningful if T<:Real Default: false
  * `ishermitian::Bool`: If the linear map is hermitian Default: false
  * `x₀::Any`: Example of vector to usen for Krylov iterations Default: nothing

## Constructors

Just pass the above fields like `EigKrylovKit(;dim=2)`
