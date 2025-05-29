```
global_position(g::BVHGraph, v::Integer, f::Integer, N::Matrix{Float64} = Matrix(1.0I, 4, 4))
```

Return the global position of vertex `v` for frame `f`.

This function does not store the result in `g`. `N` should not be changed.

See also: [`global_positions!`](@ref)
