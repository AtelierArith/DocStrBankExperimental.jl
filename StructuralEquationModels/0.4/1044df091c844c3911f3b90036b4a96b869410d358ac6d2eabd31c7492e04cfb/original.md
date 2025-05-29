```
fit([optim::SemOptimizer], model::AbstractSem;
        [engine::Symbol], start_val = start_val, kwargs...)
```

Return the fitted `model`.

# Arguments

  * `optim`: [`SemOptimizer`](@ref) to use for fitting.          If omitted, a new optimizer is constructed as `SemOptimizer(; engine, kwargs...)`.
  * `model`: `AbstractSem` to fit
  * `engine`: the optimization engine to use, default is `:Optim`
  * `start_val`: a vector or a dictionary of starting parameter values,              or function to compute them (1)
  * `kwargs...`: keyword arguments, passed to optimization engine constructor and              `start_val` function

(1) available functions are `start_fabin3`, `start_simple` and `start_partable`. For more information, we refer to the individual documentations and the online documentation on [Starting values](@ref).

# Examples

```julia
fit(my_model;
    start_val = start_simple,
    start_covariances_latent = 0.5)
```

```julia
using Optim

fit(my_model;
    algorithm = BFGS())
```
