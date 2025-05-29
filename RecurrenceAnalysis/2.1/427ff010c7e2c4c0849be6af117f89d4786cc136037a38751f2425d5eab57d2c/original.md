```
CrossRecurrenceMatrix(x, y, rthres; kwargs...)
```

Create a cross recurrence matrix from trajectories `x` and `y`. See [`RecurrenceMatrix`](@ref) for possible value for `rthres` and `kwargs`.

The cross recurrence matrix is a bivariate extension of the recurrence matrix. For the time series `x`, `y`, of length `n` and `m`, respectively, it is a sparse `n×m` matrix of Boolean values.

Note that cross recurrence matrices are generally not symmetric irrespectively of `rthres`.
