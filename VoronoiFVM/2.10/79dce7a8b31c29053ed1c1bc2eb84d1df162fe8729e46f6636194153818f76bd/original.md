```julia
mutable struct NewtonSolverHistory <: AbstractVector{Float64}
```

History information for one Newton solve of a nonlinear system. As an abstract vector it provides the history of the update norms. See [`summary`](@ref) and [`details`](@ref) for other ways to extract information.

  * `nlu::Int64`:  number of Jacobi matrix factorizations
  * `nlin::Int64`:  number of linear iteration steps / factorization solves
  * `time::Float64`:  Elapsed time for solution
  * `tasm::Float64`:  Elapsed time for assembly
  * `tlinsolve::Float64`:  Elapsed time for linear solve
  * `updatenorm::Any`:  History of norms of $||u_{i+1}-u_i||$
  * `l1normdiff::Any`:  History of norms of $|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1$
