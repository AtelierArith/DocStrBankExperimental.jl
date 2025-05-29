```
surface_grad_cross!(γ::ScalarData,ϕ::Nodes{Primal},cache::BasicILMCache)
surface_grad_cross!(γ::ScalarData,ϕ::Nodes{Primal},sys::ILMSystem)
```

The operation $\gamma = \hat{G}_s\phi = \mathbf{e}_z \cdot (\mathbf{n} \times R_f^T G\phi)$, which maps grid data `ϕ` (like scalar potential) to scalar surface data `γ` (like surface vorticity). This is the adjoint of [`surface_divergence_cross!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
