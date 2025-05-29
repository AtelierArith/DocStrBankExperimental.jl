```
normal_interpolate!(vn::ScalarData,v::Edges{Primal},cache::BasicILMCache)
normal_interpolate!(vn::ScalarData,v::Edges{Primal},sys::ILMSystem)
```

The operation $v_n = \mathbf{n} \cdot R_f^T \mathbf{v}$, which maps grid data `v` (like velocity) to scalar surface data `vn` (like normal component of surface velocity). This is the adjoint to [`regularize_normal!`](@ref).
