```
make_folds(n::Int64, k::Int64=10, k2::Int64=k)
```

Generate `k` non-overlapping folds. 

# Arguments

  * n = Total number of observations to split into folds.
  * k = Number of folds to create. Defaults to 10. If `k=1`, then all the data  (along this dimension) will be included in each fold.
  * k2 = If `k=1`, then all the data (along this dimension) will be included in  each fold. `k2` specifies how many folds there are. Defaults to `k`, which  is kind of silly, but there needs to be a placeholder.

# Value

1d array of length `k` of arrays of indices 
