```
interpolate!(f::ScalarData,s::Nodes{Primal},cache::BasicILMCache)
interpolate!(f::ScalarData,s::Nodes{Primal},sys::ILMSystem)
```

The operation $f = R_c^T s$, which interpolates scalar grid data `s` onto the surface points in the form of scalar point data `f`. This is the adjoint to [`regularize!`](@ref)
