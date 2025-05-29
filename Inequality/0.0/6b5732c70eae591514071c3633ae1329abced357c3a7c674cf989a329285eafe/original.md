lorenz(v, w) Compute the weighted Lorenz Curve of a vector `v` using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

Returns two vectors. The first one contains the cumulative proportion of weighted people.  The second contains the cumulative share of income earned.

# Examples

```julia
julia> using Inequality
julia> lorenz_curve([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9))
([0.0, 0.06666666666666667, 0.08888888888888889, 0.13333333333333333, 0.2222222222222222, 0.3333333333333333, 0.5333333333333333, 0.6666666666666666, 0.8444444444444444, 1.0],
[0.0, 0.013761467889908256, 0.05045871559633028, 0.0963302752293578, 0.1513761467889908, 0.2660550458715596, 0.38990825688073394, 0.555045871559633, 0.7752293577981653, 1.0])
```
