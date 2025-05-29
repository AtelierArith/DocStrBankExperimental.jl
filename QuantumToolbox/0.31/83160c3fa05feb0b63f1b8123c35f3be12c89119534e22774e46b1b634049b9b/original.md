```
ExponentialSeries(; tol = 1e-14, calc_steadystate = false)
```

A solver which solves [`spectrum`](@ref) by finding the eigen decomposition of the Liouvillian [`SuperOperator`](@ref) and calculate the exponential series.
