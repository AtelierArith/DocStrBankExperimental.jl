```
interpolate!(f::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
interpolate!(f::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

The operation $f = R_N^T s$, which interpolates scalar grid (curl) data `s` onto the surface points in the form of scalar point data `f`. Only works if the cache is built for vector data. This is the adjoint to [`regularize!`](@ref)
