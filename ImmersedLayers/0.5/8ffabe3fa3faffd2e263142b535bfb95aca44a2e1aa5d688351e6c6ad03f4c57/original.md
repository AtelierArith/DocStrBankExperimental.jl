```
regularize!(v::Edges{Primal},vb::VectorData,cache::BasicILMCache)
regularize!(v::Edges{Primal},vb::VectorData,sys::ILMSystem)
```

The operation $\mathbf{v} = R_f \mathbf{v}_b$, which regularizes vector surface data `vb` onto the grid in the form of scalar grid data `v`. This is the adjoint to [`interpolate!`](@ref)
