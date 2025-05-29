```
covariance_matrix(Z, W; pc::Real=0)
```

Compute the covariance matrix from numerical alignment `Z` and weights `W`. The output is a `N(q-1) × N(q-1)`  (skipping color `q`) symmetric matrix. 

## Keywords arguments:

  * `pc` in [0,1]: pseudocount [default = `0`]

end
