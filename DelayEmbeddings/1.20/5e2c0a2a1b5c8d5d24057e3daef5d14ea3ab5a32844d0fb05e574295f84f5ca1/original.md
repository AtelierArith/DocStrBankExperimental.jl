```
delay_f1nn(s::AbstractVector, τ::Int, ds = 2:6, metric = Euclidean())
```

Calculate the ratio of "false first nearest neighbors" (FFNN) of the datasets created from `s` with `embed(s, d, τ) for d ∈ ds`.

## Description

Given a dataset made by `embed(s, d, τ)` the "false first nearest neighbors" (FFNN) are the pairs of points that are nearest to each other at dimension `d` that cease to be nearest neighbors at dimension `d+1`.

The returned value is a vector with the ratio between the number of FFNN and the number of points in the dataset for each `d ∈ ds`. The optimal value for `d` is found at the point where this ratio approaches zero.

See also: [`optimal_traditional_de`](@ref).
