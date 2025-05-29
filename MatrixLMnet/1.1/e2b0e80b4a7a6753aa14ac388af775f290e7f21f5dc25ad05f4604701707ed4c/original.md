```
make_folds_conds(conds::AbstractArray{String,1}, 
                     k::Int64=10, prop::Float64=1/k)
```

Generate `k` folds for a set of conditions, making sure each level of each  condition is represented in each fold. 

# Arguments

  * conds = 1d array of conditions (strings)
  * k = Number of folds to create. Defaults to 10.
  * prop = Proportion of each condition level's replicates to include in each  fold. Defaults to 1/k. Each fold will contain at least one replicate of  each condition level.

# Value

1d array of length `k` of arrays of indices 
