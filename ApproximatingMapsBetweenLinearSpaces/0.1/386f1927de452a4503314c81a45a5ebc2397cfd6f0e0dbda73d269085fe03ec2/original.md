```
function approximate_vector(
    m::Int64,
    n::Int64,
    g::Function; # :: [-1, 1]^m -> R^n
    decomposition_method=sthosvd,
    univariate_scheme::UnivariateApproximationScheme=chebyshev(20),
    tolerance=1e-12, # Tolerance when decomposing
    kwargs...
    )::Function
```

Approximate a multivariate vector-valued function using a tensorized `univariate_approximate`. Available tensor decomposition methods are `sthosvd`, `hosvd`, `TTsvd`, `cp_als`.
