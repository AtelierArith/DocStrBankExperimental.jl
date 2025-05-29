```
ModelSelection(algorithm::AbstractString, param1::AbstractString, param2::AbstractString)
```

Returns a ModelSelection object

```
ModelSelection(algorithm::Union{Function,Nothing}
deviance::Union{Function,Real,Nothing}
r2::Union{Function,Real,Nothing}
adjr2::Union{Function,Real,Nothing}
aic::Union{Function,Real,Nothing}
bic::Union{Function,Real,Nothing}
param1::Union{Function,Real,Nothing}
param2::Union{Function,Real,Nothing})
```

For example:

```
ModelSelection("bess", "r2", "adjr2") returns
ModelSelection(BestModelSubset.best_subset, nothing, StatsAPI.r2, StatsAPI.adjr2,
               nothing, nothing, StatsAPI.r2, StatsAPI.adjr2)

ModelSelection("forward","deviance","aic")
ModelSelection(BestModelSubset.forward_stepwise, StatsAPI.deviance, nothing, nothing,
               StatsAPI.aic, nothing, StatsAPI.deviance, StatsAPI.aic)
```
