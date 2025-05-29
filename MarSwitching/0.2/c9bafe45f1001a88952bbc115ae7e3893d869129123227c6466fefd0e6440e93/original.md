```
smoothed_probs(model::MSM; kwargs...)
```

Returns smoothed probabilities of each state at each time period (Kim, 1994). If only MSM model is provided, in-sample data is used.

Smoothed probabilites, unlike filtered probabilites, are calculated using all available data.

# Arguments

  * `model::MSM`: estimated model.
  * `y`: optional data for dependent variabla.
  * `exog_vars`: optional exogenous variables for the non-switching part of the model.
  * `exog_switching_vars`: optional exogenous variables for the switching part of the model.
  * `exog_tvtp`: optional exogenous variables for the tvtp part of the model.

See also [`filtered_probs`](@ref) and [`expected_duration`](@ref).

# References

Kim, Chang Jin (1994). Dynamic Linear Models with Markov-Switching. Journal of Econometrics 60, 1-22.
