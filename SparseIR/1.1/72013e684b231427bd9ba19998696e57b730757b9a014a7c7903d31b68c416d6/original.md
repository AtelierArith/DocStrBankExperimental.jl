```
fit(sampling, al::AbstractArray{T,N}; dim=1)
```

Fit basis coefficients from the sparse sampling points Please use dim = 1 or N to avoid allocating large temporary arrays internally.
