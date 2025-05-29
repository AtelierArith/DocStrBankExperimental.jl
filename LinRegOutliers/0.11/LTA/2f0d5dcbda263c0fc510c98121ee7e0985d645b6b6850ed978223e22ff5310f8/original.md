```
lta(X, y; exact = false)
```

Perform the Hawkins & Olive (1999) algorithm (Least Trimmed Absolute Deviations)  for the given regression setting.

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix of linear regression model.
  * `y::AbstractVector{Float64}`: Response vector of linear regression model.
  * `exact::Bool`: Consider all possible subsets of p or not where p is the number of regression parameters.
  * `earlystop::Bool`: Early stop if the best objective does not change in number of remaining iters / 5 iterations.

# References

Hawkins, Douglas M., and David Olive. "Applications and algorithms for least trimmed sum of  absolute deviations regression." Computational Statistics & Data Analysis 32.2 (1999): 119-134.
