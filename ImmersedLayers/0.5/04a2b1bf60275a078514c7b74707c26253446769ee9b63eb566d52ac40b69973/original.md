```
surface_divergence!(Θ::Nodes{Primal},f::ScalarData,cache::BasicILMCache)
surface_divergence!(Θ::Nodes{Primal},f::ScalarData,sys::ILMSystem)
```

The operation $\theta = D_s f = D R_f \mathbf{n} \circ f$, which maps surface scalar data `f` (like jump in scalar potential) to grid data `Θ` (like dilatation, i.e. divergence of velocity). This is the negative adjoint of [`surface_grad!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
