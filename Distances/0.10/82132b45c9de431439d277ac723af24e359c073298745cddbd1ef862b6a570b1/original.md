```
colwise!(r::AbstractArray, dist::PreMetric, a, b)
```

Same as `colwise!(dist, r, a, b)`.

!!! warning
    Since this alternative syntax is deprecated and will be removed in a future release of Distances.jl, its use is discouraged. Please call `colwise!(dist, r, a, b)` instead.

