```
surface_curl!(v::VectorData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl!(v::VectorData,s::Nodes{Dual},sys::ILMSystem)
```

The operation $\mathbf{v} = C_s s = R_f^T C s$, which maps grid data `s` (like streamfunction) to vector surface data `v` (like velocity). This is the adjoint to $C_s^T$, also given by `surface_curl!`, but with arguments switched.  Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
