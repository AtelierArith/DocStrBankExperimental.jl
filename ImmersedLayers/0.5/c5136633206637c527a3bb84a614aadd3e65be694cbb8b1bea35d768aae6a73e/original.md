```
normal_cross_interpolate!(vs::VectorData,s::Nodes{Dual},cache::BasicILMCache)
normal_cross_interpolate!(vs::VectorData,s::Nodes{Dual},sys::ILMSystem)
```

The operation $\mathbf{v}_s = \mathbf{n}\times R_N^T \psi\mathbf{e}_z)$, which maps grid data `s` (like streamfunction) to vector surface data `vs` (like velocity in the surface). It only works for a vector-type cache. This is the negative adjoint to [`regularize_normal_cross!`](@ref).
