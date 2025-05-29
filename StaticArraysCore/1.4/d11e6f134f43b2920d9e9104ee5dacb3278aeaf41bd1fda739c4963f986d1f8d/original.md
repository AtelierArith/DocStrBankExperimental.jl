```
SizedMatrix{S1,S2,T} = SizedArray{Tuple{S1,S2},T,2}
```

Wraps a two-dimensional `AbstractArray` with static dimensions `S1` by `S2` and element type `T`, leveraging the performance optimizations of StaticArrays.jl.

For detailed usage and functionality, refer to the documentation of `SizedArray`.
