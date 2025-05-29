```
regularize_normal_dot!(f::Nodes{Primal},vs::VectorData,cache::BasicILMCache)
regularize_normal_dot!(f::Nodes{Primal},vs::VectorData,sys::ILMSystem)
```

The operation $\phi = R_c \mathbf{n}\cdot \mathbf{v}_s$, which maps surface vector data `vs` (like a jump in velocity) to grid nodal data `f` (like scalar potential). This is the negative adjoint to [`normal_dot_interpolate!`](@ref).
