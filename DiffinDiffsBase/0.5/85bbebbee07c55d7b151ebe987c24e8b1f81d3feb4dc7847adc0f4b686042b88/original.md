```
istreated!(out::AbstractVector{Bool}, pr::TrendParallel, x::AbstractArray)
```

For each element in `x`, test whether it represents the treatment time for a group of units that are not treated and save the result in `out`. See also [`istreated`](@ref).
