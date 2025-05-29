```
regularize!(s::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
regularize!(s::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

The operation $s = R_N f$, which regularizes scalar surface data `f` onto the grid in the form of scalar grid (curl) data `s`. Only works if the cache is built for vector data. This is the adjoint to [`interpolate!`](@ref)
