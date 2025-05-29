```
function loo_compare(
    cv_results...;
    sort_models::Bool=true,
    best_to_worst::Bool=true,
    [, model_names::Tuple{Symbol}]
) -> ModelComparison
```

Construct a model comparison table from several [`PsisLoo`](@ref) objects.

# Arguments

  * `cv_results`: One or more [`PsisLoo`](@ref) objects to be compared. Alternatively, a tuple or named tuple of `PsisLoo` objects can be passed. If a named tuple is passed, these names will be used to label each model.
  * `model_names`: A vector or tuple of strings or symbols used to identify models. If none, models are numbered using the order of the arguments.
  * `sort_models`: Sort models by total score.
  * `high_to_low`: Sort models from best to worst score. If `false`, reverse the order.

See also: [`ModelComparison`](@ref), [`PsisLoo`](@ref), [`psis_loo`](@ref)
