```
latglq, longlq, nlat, nlong =
    GLQGridCoord!(latglq::AbstractVector{Cdouble},
                  longlq::AbstractVector{Cdouble},
                  lmax::Integer;
                  extend::Integer=0,
                  exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
latglq::AbstractVector{Cdouble},
longlq::AbstractVector{Cdouble},
nlat::Int
nlong::Int
```

Compute the latitude and longitude coordinates used in Gauss-Legendre quadrature grids.

See also: [`GLQGridCoord`](@ref), [`SHExpandGLQ!`](@ref), [`MakeGridGLQ!`](@ref)
