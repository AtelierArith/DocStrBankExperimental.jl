```
StopWhenCovarianceIllConditioned <: StoppingCriterion
```

Stop CMA-ES if condition number of covariance matrix exceeds `threshold`. This corresponds to `ConditionCov` condition from [Hansen:2023](@cite).
