```
regularize_normal_symm!(qt::EdgeGradient{Primal},v::VectorData,cache::BasicILMCache)
regularize_normal_symm!(qt::EdgeGradient{Primal},v::VectorData,sys::ILMSystem)
```

The operation $\mathbf{q}_t = R_t (\mathbf{n}\circ \mathbf{v}+\mathbf{v}\circ \mathbf{n})$, which maps scalar vector data `v` (like a jump in velocity) to grid data `qt` (like velocity-normal tensor). This is the adjoint to [`normal_interpolate_symm!`](@ref).
