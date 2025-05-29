```
SizedVector{S, T} = SizedArray{Tuple{S}, T, 1, 1}
```

Wraps a one-dimensional `AbstractArray` with static length `S` and element type `T`, leveraging the performance optimizations of StaticArrays.jl.

For detailed usage and functionality, refer to the documentation of `SizedArray`.
