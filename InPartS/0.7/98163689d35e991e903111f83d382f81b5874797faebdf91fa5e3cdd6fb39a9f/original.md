```
forcecontribution(c::SVector{2, T}, f::SVector{2, T}, δ::SVector{2, T}) where {T}
forcecontribution(c::SVector{3, T}, f::SVector{3, T}, δ::SVector{3, T}) where {T}
```

Returns a named tuple containing the individual components of `c`, `f` and `δ`.

In the 2D case, the names of the tuple entries are `cx`, `cy`, `fx`, `fy` and `δx`, `δy`; in 3D, the additional entries are called `cz`, `fz` and `δz` respectively

Useful for force accumulation using [`@forcedef`](@ref).
