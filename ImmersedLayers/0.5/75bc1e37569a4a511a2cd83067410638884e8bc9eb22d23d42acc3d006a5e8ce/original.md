```
normal_interpolate_symm!(τ::VectorData,A::EdgeGradient{Primal},cache::BasicILMCache)
normal_interpolate_symm!(τ::VectorData,A::EdgeGradient{Primal},sys::ILMSystem)
```

The operation $\mathbf{\tau} = \mathbf{n} \cdot R_t^T (\mathbf{A} +\mathbf{A}^T - (\mathrm{tr}\mathbf{A})\mathbf{I})$, which maps grid tensor data `A` (like velocity gradient tensor) to vector surface data `τ` (like traction). This is the adjoint to [`regularize_normal_symm!`](@ref).
