```
contrast(anovaresult::AnovaResult, groupassignment::Vector{Int})
```

Calculate a single-factor contrast against the groups specified in `groupassignment`. Valid groups are "0", "1", and "2", where "0" excludes the group from the comparison.

Note: If you do nonorthogonal contrasts, use the Bonferroni or Šidák correction to adjust the α level (the level at which you consider a result likely to be true):   Bonferroni: α′ = α/c for c contrasts   Šidák:      α′ = 1 - (1 - α)^(1 / c) (slightly better) where c = number of contrasts

Note: Effect size is calcluated using the error term associated with the factor. Other choices are possible, including average of each group error; or the error associated with a control.
