```
surface_divergence!(v::Edges{Primal},dv::VectorData,cache::BasicILMCache)
surface_divergence!(v::Edges{Primal},dv::VectorData,sys::ILMSystem)
```

The operation $\mathbf{v} = D_s d\mathbf{v} = D R_t (\mathbf{n} \circ d\mathbf{v})$, which maps surface vector data `dv` (like jump in velocity) to grid data `v` (like velocity). This is the negative adjoint of [`surface_grad!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
