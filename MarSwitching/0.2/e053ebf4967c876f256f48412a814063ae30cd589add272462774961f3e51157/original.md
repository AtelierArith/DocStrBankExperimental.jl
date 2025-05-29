```
filtered_probs(model::MSM; kwargs...)
```

Returns filtered probabilities of each state at each time period. If only model is provided, in-sample data is used.

Filtered probabilites, unlike smoothed probabilites, are calculated using data available up to time T.

# Arguments

  * `model::MSM`: estimated model.
  * `y`: optional data for dependent variabla.
  * `exog_vars`: optional exogenous variables for the non-switching part of the model.
  * `exog_switching_vars`: optional exogenous variables for the switching part of the model.
  * `exog_tvtp`: optional exogenous variables for the tvtp part of the model.

See also [`smoothed_probs`](@ref) and [`expected_duration`](@ref).
