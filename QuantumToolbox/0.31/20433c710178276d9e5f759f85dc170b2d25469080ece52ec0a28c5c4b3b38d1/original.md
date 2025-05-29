```
struct TimeEvolutionLRSol
```

A structure storing the results and some information from solving low-rank master equation time evolution.

# Fields (Attributes)

  * `times::AbstractVector`: The time list of the evolution.
  * `states::Vector{QuantumObject}`: The list of result states.
  * `expect::Matrix`: The expectation values corresponding to each time point in `times`.
  * `fexpect::Matrix`: The function values at each time point.
  * `retcode`: The return code from the solver.
  * `alg`: The algorithm which is used during the solving process.
  * `abstol::Real`: The absolute tolerance which is used during the solving process.
  * `reltol::Real`: The relative tolerance which is used during the solving process.
  * `z::Vector{QuantumObject}`: The `z`` matrix of the low-rank algorithm at each time point.
  * `B::Vector{QuantumObject}`: The `B` matrix of the low-rank algorithm at each time point.
