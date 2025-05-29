```
normal_dot_interpolate!(taus::TensorData,v::Edges{Primal},cache::BasicILMCache)
normal_dot_interpolate!(taus::TensorData,v::Edges{Primal},sys::ILMSystem)
```

The operation $\mathbf{\tau}_s = \mathbf{n}\circ R_f^T\mathbf{v}$, which maps grid edge data `v` (like velocity) to surface tensor data `taus` (like stress). This is the negative adjoint to [`regularize_normal_dot!`](@ref).
