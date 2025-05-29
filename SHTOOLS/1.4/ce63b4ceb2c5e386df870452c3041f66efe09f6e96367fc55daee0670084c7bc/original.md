```
zero, w = SHGLQ(plx::Union{Nothing,AbstractArray{Cdouble,2}},
                lmax::Integer;
                norm::Integer=1,
                csphase::Integer=1,
                cnorm::Integer=0,
                exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
zero::Vector{Cdouble}
w::Vector{Cdouble}
```

Precompute weights, nodes, and associated Legendre functions used in the GLQ-based spherical harmonics routines.

See also: [`SHGLQ!`](@ref), [`SHExpandGLQ`](@ref), [`MakeGridGLQ`](@ref), [`GLQGridCoord`](@ref)
