```
StatsAPI.predict(m::LinearMixedModel, newdata;
                new_re_levels=:missing)
StatsAPI.predict(m::GeneralizedLinearMixedModel, newdata;
                new_re_levels=:missing, type=:response)
```

Predict response for new data.

!!! note
    Currently, no in-place methods are provided because these methods internally construct a new model and therefore allocate not just a response vector but also many other matrices.


!!! warning
    `newdata` should contain a column for the response (dependent variable) initialized to some numerical value (not `missing`), because this is used to construct the new model used in computing the predictions. `missing` is not valid because `missing` data are dropped before constructing the model matrices.


!!! warning
    These methods construct an entire MixedModel behind the scenes and as such may use a large amount of memory when `newdata` is large.


!!! warning
    Rank-deficiency can lead to surprising but consistent behavior. For example, if there are two perfectly collinear predictors `A` and `B` (e.g. constant multiples of each other), then it is possible that `A` will be pivoted out in the fitted model and thus the associated coefficient is set to zero. If predictions are then generated on new data where `B` has been set to zero but `A` has not, then there will no contribution from neither `A` nor `B` in the resulting predictions.


The keyword argument `new_re_levels` specifies how previously unobserved values of the grouping variable are handled. Possible values are:

  * `:population`: return population values for the relevant grouping variable.  In other words, treat the associated random effect as 0.  If all grouping variables have new levels, then this is equivalent to  just the fixed effects.
  * `:missing`: return `missing`.
  * `:error`: error on this condition. The error type is an implementation detail:  you should not rely on a particular type of error being thrown.

If you want simulated values for unobserved levels of the grouping variable, consider the [`simulate!`](@ref) and `simulate` methods.

Predictions based purely on the fixed effects can be obtained by specifying previously unobserved levels of the random effects and setting `new_re_levels=:population`. Similarly, the contribution of any grouping variable can be excluded by specifying previously unobserved levels, while including previously observed levels of the other grouping variables. In the future, it may be possible to specify a subset of the grouping variables or overall random-effects structure to use, but not at this time.

!!! note
    `new_re_levels` impacts only the behavior for previously unobserved random effects levels, i.e. new RE levels. For previously observed random effects levels, predictions take both the fixed and random effects into account.


For `GeneralizedLinearMixedModel`, the `type` parameter specifies whether the predictions should be returned on the scale of linear predictor (`:linpred`) or on the response scale (`:response`). If you don't know the difference between these terms, then you probably want `type=:response`.

Regression weights are not yet supported in prediction. Similarly, offsets are also not supported for `GeneralizedLinearMixedModel`.
