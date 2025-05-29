```
surface_curl_cross!(w::Nodes{Dual},f::ScalarData,cache::BasicILMCache)
surface_curl_cross!(w::Nodes{Dual},f::ScalarData,sys::ILMSystem)
```

The operation $w = \hat{C}_s^T f = C^T R_f \mathbf{n}\times f \mathbf{e}_z$, which maps scalar surface data `f` (like a jump in streamfunction, multiplied by out-of-plane unit vector $\mathbf{e}_z$) to grid data `w` (like vorticity). This is the adjoint to $\hat{C}_s$, also given by `surface_curl_cross!` (but with arguments switched). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
