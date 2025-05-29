```
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,cache::BasicILMCache)
regularize_normal_cross!(v::Edges{Primal},f::ScalarData,sys::ILMSystem)
```

The operation $\mathbf{v} = R_f \mathbf{n}\times f \mathbf{e}_z$, which maps scalar surface data `f` (like a jump in streamfunction, endowed with the out-of-plane unit vector $\mathbf{e}_z$) to grid data `v` (like velocity). This is the negative adjoint to [`normal_cross_interpolate!`](@ref).
