```
struct TimeEvolutionSol
```

A structure storing the results and some information from solving time evolution.

# Fields (Attributes)

  * `times::AbstractVector`: The time list of the evolution.
  * `states::Vector{QuantumObject}`: The list of result states.
  * `expect::Union{AbstractMatrix,Nothing}`: The expectation values corresponding to each time point in `times`.
  * `retcode`: The return code from the solver.
  * `alg`: The algorithm which is used during the solving process.
  * `abstol::Real`: The absolute tolerance which is used during the solving process.
  * `reltol::Real`: The relative tolerance which is used during the solving process.
