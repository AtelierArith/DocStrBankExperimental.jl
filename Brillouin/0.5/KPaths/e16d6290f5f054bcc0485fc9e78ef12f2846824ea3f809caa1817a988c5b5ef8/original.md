```
splice(kvs::AbstractVector{<:AbstractVector{<:Real}}, N::Integer)
                                                --> Vector{Vector{<:Real}}
```

Return an interpolated **k**-path between the discrete **k**-points in `kvs`, with `N` interpolation points inserted in each segment defined by pairs of adjacent **k**-points.

See also [`splice(::KPath, ::Integer)`](@ref) and [`interpolate`](@ref).

!!! warning "Future deprecation"
    This method signature is likely to be deprecated in future versions of Brillouin.jl.

