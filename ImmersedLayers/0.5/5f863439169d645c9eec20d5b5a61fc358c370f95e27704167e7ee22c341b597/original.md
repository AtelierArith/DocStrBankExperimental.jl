```
regularize!(s::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
regularize!(s::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

The operation $s = R_c f$, which regularizes scalar surface data `f` onto the grid in the form of scalar grid data `s`. This is the adjoint to [`interpolate!`](@ref)
