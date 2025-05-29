```
normal_cross_interpolate!(wn::ScalarData,v::Edges{Primal},cache::BasicILMCache)
normal_cross_interpolate!(wn::ScalarData,v::Edges{Primal},sys::ILMSystem)
```

The operation $w_n = e_z\cdot (\mathbf{n} \times R_f^T \mathbf{v})$, which maps grid data `v` (like velocity) to scalar surface data `wn` (like vorticity in the surface). This is the negative adjoint to [`regularize_normal_cross!`](@ref).
