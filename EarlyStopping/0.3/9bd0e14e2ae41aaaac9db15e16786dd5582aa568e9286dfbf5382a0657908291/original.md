```
NumberSinceBest(; n=6)
```

An early stopping criterion for loss-reporting iterative algorithms. 

A stop is triggered when the number of calls to the control, since the lowest value of the loss so far, is `n`.

For a customizable loss-based stopping criterion, use [`WithLossDo`](@ref) or [`WithTrainingLossesDo`](@ref) with the `stop_if_true=true` option. 
