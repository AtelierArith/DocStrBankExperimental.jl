```
regularize_normal_cross!(w::Nodes{Dual},vs::VectorData,cache::BasicILMCache)
regularize_normal_cross!(w::Nodes{Dual},vs::VectorData,sys::ILMSystem)
```

The operation $\omega = R_N \mathbf{n}\times \mathbf{v}_s$, which maps surface vector data `vs` (like a jump in velocity) to grid dual nodal data `w` (like vorticity). This is for use only with vector-data caches. This is the negative adjoint to [`normal_cross_interpolate!`](@ref).
