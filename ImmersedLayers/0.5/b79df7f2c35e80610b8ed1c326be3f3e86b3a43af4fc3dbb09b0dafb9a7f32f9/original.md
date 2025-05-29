```
regularize_normal_dot!(v::Edges{Primal},taus::TensorData,cache::BasicILMCache)
regularize_normal_dot!(v::Edges{Primal},taus::TensorData,sys::ILMSystem)
```

The operation $\mathbf{v} = R_f \mathbf{n}\cdot \mathbf{\tau}_s$, which maps surface tensor data `taus` (like a stress) to grid edge data `v` (like velocity). This is the negative adjoint to [`normal_dot_interpolate!`](@ref).
