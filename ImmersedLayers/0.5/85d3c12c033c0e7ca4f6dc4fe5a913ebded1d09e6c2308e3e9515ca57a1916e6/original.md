```
surface_curl!(vn::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl!(vn::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

The operation $v_n = C_s s = \mathbf{n} \cdot R_f^T C s$, which maps grid data `s` (like streamfunction) to scalar surface data `vn` (like normal component of velocity). This is the adjoint to $C_s^T$, also given by `surface_curl!`, but with arguments switched.  Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
