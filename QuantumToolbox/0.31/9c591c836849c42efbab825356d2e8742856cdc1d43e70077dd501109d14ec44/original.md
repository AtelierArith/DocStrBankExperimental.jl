```
struct TimeEvolutionStochasticSol
```

A structure storing the results and some information from solving trajectories of the Stochastic time evolution.

# Fields (Attributes)

  * `ntraj::Int`: Number of trajectories
  * `times::AbstractVector`: The time list of the evolution.
  * `states::Vector{Vector{QuantumObject}}`: The list of result states in each trajectory.
  * `expect::Union{AbstractMatrix,Nothing}`: The expectation values (averaging all trajectories) corresponding to each time point in `times`.
  * `average_expect::Union{AbstractMatrix,Nothing}`: The expectation values (averaging all trajectories) corresponding to each time point in `times`.
  * `runs_expect::Union{AbstractArray,Nothing}`: The expectation values corresponding to each trajectory and each time point in `times`
  * `converged::Bool`: Whether the solution is converged or not.
  * `alg`: The algorithm which is used during the solving process.
  * `abstol::Real`: The absolute tolerance which is used during the solving process.
  * `reltol::Real`: The relative tolerance which is used during the solving process.
