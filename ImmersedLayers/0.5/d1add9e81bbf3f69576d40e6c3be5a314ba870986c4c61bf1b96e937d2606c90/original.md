```
interpolate!(vb::VectorData,v::Edges{Primal},cache::BasicILMCache)
interpolate!(vb::VectorData,v::Edges{Primal},sys::ILMSystem)
```

The operation $\mathbf{v}_b = R_c^T \mathbf{v}$, which interpolates vector grid data `v` onto the surface points in the form of scalar point data `vb`. This is the adjoint to [`regularize!`](@ref)
