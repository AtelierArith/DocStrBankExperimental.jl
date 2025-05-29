```
cilm = SHExpandGLQ(lmax::Integer,
                   gridglq::AbstractArray{Cdouble,2},
                   w::AbstractVector{Cdouble},
                   plx::Union{Nothing,AbstractArray{Cdouble,2}},
                   zero::Union{Nothing,AbstractVector{Cdouble}};
                   norm::Integer=1,
                   csphase::Integer=1,
                   lmax_calc::Union{Nothing,Integer}=nothing,
                   exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3},

cilm = SHExpandGLQ(lmax::Integer,
                   gridglq::AbstractArray{Complex{Cdouble},2},
                   w::AbstractVector{Cdouble},
                   plx::Union{Nothing,AbstractArray{Cdouble,2}},
                   zero::Union{Nothing,AbstractVector{Cdouble}};
                   norm::Integer=1,
                   csphase::Integer=1,
                   lmax_calc::Union{Nothing,Integer}=nothing,
                   exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Complex{Cdouble},3},
```

Expand a 2D real or complex map sampled on the Gauss-Legendre quadrature nodes into real or complex spherical harmonics.

See also: [`SHExpandGLQ!`](@ref), [`SHGLQ`](@ref), [`MakeGridGLQ`](@ref), [`GLQGridCoord`](@ref)
