```
zonalmean(A::ClimArray [, W])
```

Return the zonal mean of `A`. Works for both [`OrthogonalSpace`](@ref) as well as [`CoordinateSpace`](@ref). Optionally provide statistical weights `W`. These can be the same `size` as `A` or only having the same latitude structure as `A`.
