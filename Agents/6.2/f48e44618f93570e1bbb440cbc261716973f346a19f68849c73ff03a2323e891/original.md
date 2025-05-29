```
ensemblerun!(models::Vector, n; kwargs...)
```

Perform an ensemble simulation of [`run!`](@ref) for all `model ∈ models`. Each `model` should be a (different) instance of an [`AgentBasedModel`](@ref) but probably initialized with a different random seed or different initial agent distribution. All models obey the same evolution rules contained in  the model and are evolved for `n`.

Similarly to [`run!`](@ref) this function will collect data. It will furthermore add one additional column to the dataframe called `:ensemble`, which has an integer value counting the ensemble member. The function returns `agent_df, model_df, models`.

If you want to scan parameters and at the same time run multiple simulations at each parameter combination, simply use `seed` as a parameter, and use that parameter to tune the model's initial random seed and/or agent distribution.

See example usage in [Schelling's segregation model](@ref Tutorial).

## Keywords

The following keywords modify the `ensemblerun!` function:

  * `parallel::Bool = false` whether `Distributed.pmap` is invoked to run simulations in parallel. This must be used in conjunction with `@everywhere` (see [Performance Tips](@ref)).
  * `showprogress::Bool = false` whether a progressbar will be displayed to indicate % runs finished.

All other keywords are propagated to [`run!`](@ref) as-is.
