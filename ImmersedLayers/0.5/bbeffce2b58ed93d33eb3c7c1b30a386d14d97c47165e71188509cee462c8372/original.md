```
surface_curl!(w::Nodes{Dual},v::VectorData,cache::BasicILMCache)
surface_curl!(w::Nodes{Dual},v::VectorData,sys::ILMSystem)
```

The operation $w = C_s^T \mathbf{v} = C^T R_f \mathbf{v}$, which maps vector surface data `v` (like velocity) to grid data `w` (like vorticity). This is the adjoint to $C_s$, also given by `surface_curl!` (but with arguments switched). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
