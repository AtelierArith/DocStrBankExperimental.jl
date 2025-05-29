```
Threshold(; value=0.0)
```

An early stopping criterion for loss-reporting iterative algorithms. 

A stop is triggered as soon as the loss drops below `value`.

For a customizable loss-based stopping criterion, use [`WithLossDo`](@ref) or [`WithTrainingLossesDo`](@ref) with the `stop_if_true=true` option. 
