```
ErrorPropagator([::Type{T}; N_args, capacity::Int])
```

Creates an `ErrorPropagator` which can handle (at least) `capacity` many values for each of `N_args` inputs of type `T`.

The default is `T = Float64`, `N_args = 2` and `capacity = 2^32-1 ≈ 4e9`.
