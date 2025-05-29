```
OptimizationAM(; kwargs...)
```

Maximizes the acquisition function using the Optimization.jl library.

Can handle constraints on `x` if according optimization algorithm is selected.

# Keywords

  * `algorithm::Any`: Defines the optimization algorithm.
  * `multistart::Union{<:Int, <:AbstractMatrix{<:Real}}`: The number of optimization restarts,       or a matrix of optimization intial points as columns.
  * `parallel::Bool`: If `parallel=true` then the individual restarts are run in parallel.
  * `autodiff:SciMLBase.AbstractADType:`: The automatic differentiation module       passed to `Optimization.OptimizationFunction`.
  * `kwargs...`: Other kwargs are passed to the optimization algorithm.
