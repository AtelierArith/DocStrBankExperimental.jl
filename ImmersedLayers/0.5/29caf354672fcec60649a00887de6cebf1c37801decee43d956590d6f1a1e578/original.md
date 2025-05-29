```
surface_curl_cross!(γ::ScalarData,s::Nodes{Dual},cache::BasicILMCache)
surface_curl_cross!(γ::ScalarData,s::Nodes{Dual},sys::ILMSystem)
```

The operation $\gamma = \hat{C}_s s = \mathbf{e}_z\cdot (\mathbf{n} \times R_f^T C s)$, which maps grid data `s` (like streamfunction) to scalar surface data `γ` (like vorticity in the surface). This is the adjoint to $\hat{C}_s^T$, also given by `surface_curl_cross!`, but with arguments switched.  Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
