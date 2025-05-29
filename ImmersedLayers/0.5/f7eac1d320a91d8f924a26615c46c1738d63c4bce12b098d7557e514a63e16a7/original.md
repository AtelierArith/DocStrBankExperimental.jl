```
surface_divergence_cross!(Θ::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
surface_divergence_cross!(Θ::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

The operation $\theta = \hat{D}_s f = D R_f \mathbf{n} \times f \mathbf{e}_z$, which maps surface scalar data `f` (like jump in streamfunction) to grid data `Θ` (like dilatation, i.e. divergence of velocity). This is the adjoint of [`surface_grad_cross!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
