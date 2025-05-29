```
create_re(sigmas...; corrmat=Matrix{Float64}(I, length(sigmas), length(sigmas))
```

Create the covariance factor for a random effect from the standard deviations and correlation matrix.

The `sigmas` should be specified in the same order as the random slopes in the output of `VarCorr(m)`.

!!! note
    The `sigmas` are specified **relative** to the residual standard deviation.  Absolute values must be scaled by dividing by the assumed residual  standard deviation.


The correlation matrix defaults to the identity matrix, i.e. no correlation between random effects.

!!! note
    The return value is the lower Cholesky factor of the covariance matrix, which is what [`update!`](@ref) requires.

