```
InvalidValue()
```

An early stopping criterion for loss-reporting iterative algorithms. 

Stop if a loss (or training loss) is `NaN`, `Inf` or `-Inf` (or, more precisely, if `isnan(loss)` or `isinf(loss)` is `true`).

For a customizable loss-based stopping criterion, use [`WithLossDo`](@ref) or [`WithTrainingLossesDo`](@ref) with the `stop_if_true=true` option. 
