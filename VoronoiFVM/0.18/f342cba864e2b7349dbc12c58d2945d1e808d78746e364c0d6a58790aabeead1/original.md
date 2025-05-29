```julia
mutable struct NewtonSolverHistory <: AbstractVector{Float64}
```

History information for one Newton solve of a nonlinear system. As an abstract vector it provides the history of the update norms. See [`summary`](@ref) and [`details`](@ref) for other ways to extract information.

  * `nlu::Int64`:  number of Jacobi matrix factorizations  Default: 0
  * `nlin::Int64`:  number of linear interation steps / factorization solves Default: 0
  * `time::Float64`:  Elapsed time for solution  Default: 0.0
  * `updatenorm::Any`:  History of norms of $||u_{i+1}-u_i||$ Default: zeros(0)
  * `l1normdiff::Any`:  History of norms of $|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1$  Default: zeros(0)
