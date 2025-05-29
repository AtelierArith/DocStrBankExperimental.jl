```julia
construct_interpolations(x, y; method, order, extrapolation)

```

Construct interpolation of a nested array. If `x` is an `AbstractRange`, the nested array will be converted into multi-dimensional array for interpolation. Otherwise only "Gridded" method and `order` 1 is supported.
