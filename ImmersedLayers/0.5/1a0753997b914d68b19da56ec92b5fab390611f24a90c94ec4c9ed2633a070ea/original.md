```
normal_dot_interpolate!(vs::VectorData,f::Nodes{Primal},cache::BasicILMCache)
normal_dot_interpolate!(vs::VectorData,f::Nodes{Primal},sys::ILMSystem)
```

The operation $\mathbf{v}_s = \mathbf{n} R_c^T \phi$, which maps grid nodal data `f` (like scalar potential) to surface vector data `vs` (like velocity). This is the negative adjoint to [`regularize_normal_dot!`](@ref).
