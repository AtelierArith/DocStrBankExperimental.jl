```
regularize_normal!(v::Edges{Primal},f::ScalarData,cache::BasicILMCache)
regularize_normal!(v::Edges{Primal},f::ScalarData,sys::ILMSystem)
```

The operation $\mathbf{v} = R_f \mathbf{n}\circ f$, which maps scalar surface data `f` (like a jump in scalar potential) to grid data `v` (like velocity). This is the adjoint to [`normal_interpolate!`](@ref).
