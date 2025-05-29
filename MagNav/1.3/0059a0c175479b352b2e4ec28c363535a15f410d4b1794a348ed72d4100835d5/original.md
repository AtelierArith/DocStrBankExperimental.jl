```
detrend(y, x = [eachindex(y);]; λ = 0, mean_only::Bool = false)
```

Detrend signal (remove mean and optionally slope).

**Arguments:**

  * `y`:         length-`N` observed data vector
  * `x`:         (optional) `N` x `Nf` input data matrix (`Nf` is number of features)
  * `λ`:         (optional) ridge parameter
  * `mean_only`: (optional) if true, only remove mean (not slope)

**Returns:**

  * `y`: length-`N` observed data vector, detrended
