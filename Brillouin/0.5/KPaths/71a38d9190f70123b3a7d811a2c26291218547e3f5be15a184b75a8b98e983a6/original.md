```
interpolate(kvs::AbstractVector{<:AbstractVector{<:Real}}, N::Integer)
                                                --> Vector{Vector{<:Real}}
```

Return an interpolated **k**-path between discrete **k**-points in `kvs`, with approximately `N` interpolation points in total (typically fewer).

Note that, in general, it is not possible to do this so that all interpolated **k**-points are equidistant; samples are however *exactly* equidistant across each linear segment defined by points in `kvs` and *approximately* equidistant across all segments.

See also [`interpolate(::KPath, ::Integer)`](@ref) and [`splice`](@ref).

!!! warning "Future deprecation"
    This method signature is likely to be deprecated in future versions of Brillouin.jl.

