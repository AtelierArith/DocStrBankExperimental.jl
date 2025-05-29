```
predict(model::MSM, instantaneous::Bool = false; kwargs...)
```

Provide either instantaneous or one-step-ahead prediction of the dependent variable.    

Which is the probability weighted average of predictions of each state equation:

$$
\hat{y}_t = \sum_{i=1}^{k} \hat{\xi}_{i,t}X_{t}'\hat{\beta}_{i}
$$

And for one step ahead, the state probabilities have to be predicted themselves:

$$
\hat{y}_{t+1} = \sum_{i=1}^{k} (P\hat{\xi}_{i,t})X_{t+1}'\hat{\beta}_{i}
$$

If only MSM model is provided, in-sample data is used.

Returns a tuple of `(ŷ, ξ_t)` where `ŷ` is the predicted value of the dependent variable and `ξ_t` is the filtered probabilities of each state at each time period.

# Arguments

  * `model::MSM`: estimated model.
  * `y`: optional data for dependent variabla.
  * `exog_vars`: optional exogenous variables for the non-switching part of the model.
  * `exog_switching_vars`: optional exogenous variables for the switching part of the model.
  * `exog_tvtp`: optional exogenous variables for the tvtp part of the model.
