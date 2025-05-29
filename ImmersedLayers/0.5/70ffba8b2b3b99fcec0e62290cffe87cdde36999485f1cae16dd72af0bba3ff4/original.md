```
surface_grad!(vn::ScalarData,ϕ::Nodes{Primal},cache::BasicILMCache)
surface_grad!(vn::ScalarData,ϕ::Nodes{Primal},sys::ILMSystem)
```

The operation $v_n = G_s\phi = \mathbf{n} \cdot R_f^T G\phi$, which maps grid data `ϕ` (like scalar potential) to scalar surface data `vn` (like normal component of velocity). This is the negative adjoint of [`surface_divergence!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
