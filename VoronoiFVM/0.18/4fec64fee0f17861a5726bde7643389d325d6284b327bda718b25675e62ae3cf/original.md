```julia
mutable struct TransientSolverHistory <: AbstractVector{VoronoiFVM.NewtonSolverHistory}
```

History information for transient solution/parameter embedding

As an abstract vector it provides the histories of each implicit Euler/embedding step. See [`summary`](@ref) and [`details`](@ref) for other ways to extract information.

  * `histories::Any`:  Histories of each implicit Euler Newton iteration  Default: Vector{NewtonSolverHistory}(undef, 0)
  * `times::Any`:  Time values  Default: zeros(0)
  * `updates::Any`:  Update norms used for step control Default: zeros(0)
