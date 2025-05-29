```
soft_assignment(conf_model::ConformalProbabilisticSet, fitresult, X; temp::Real=0.1)
```

This function can be used to compute soft assigment probabilities for new data `X` as in [`soft_assignment(conf_model::ConformalProbabilisticSet; temp::Real=0.1)`](@ref). When a fitted model $\mu$ (`fitresult`) and new samples `X` are supplied, non-conformity scores are first computed for the new data points. Then the existing threshold/quantile `q̂` is used to compute the final soft assignments. 
