```
surface_grad!(τ::VectorData,v::Edges{Primal},cache::BasicILMCache)
surface_grad!(τ::VectorData,v::Edges{Primal},sys::ILMSystem)
```

The operation $\mathbf{\tau} = G_s v = \mathbf{n} \cdot R_t^T G \mathbf{v}$, which maps grid vector data `v` (like velocity) to vector surface data `τ` (like traction). This is the negative adjoint of [`surface_divergence!`](@ref). Note that the differential operations are divided either by 1 or by the grid cell size, depending on whether `sys` has been designated with `IndexScaling` or `GridScaling`, respectively.
