```
surface_curl!(w::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
surface_curl!(w::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

The operation $w = C_s^T f = C^T R_f \mathbf{n}\circ f$, which maps scalar surface data `f` (like a jump in scalar potential) to grid data `w` (like vorticity). This is the adjoint to $C_s$, also given by `surface_curl!` (but with arguments switched). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
