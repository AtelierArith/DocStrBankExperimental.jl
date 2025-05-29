```
JointStratifiedCV(;patterns=nothing, resampling=StratifiedCV())
```

Applies a stratified cross-validation strategy based on a variable constructed from X and y.  A composite variable is built from: 

  * x variables from X matching any of `patterns` and satisfying `autotype(x) <: Union{Missing, Finite}`.

If no pattern is provided, then only the second condition is considered.

  * y if `autotype(y) <: Union{Missing, Finite}`

The `resampling` needs to be a stratification compliant resampling strategy, at the moment  one of `StratifiedCV` or `AdaptiveStratifiedCV`
