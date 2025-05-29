```
cilm, chi = SHExpandLSQ!(cilm::AbstractArray{Cdouble,3},
                         d::AbstractVector{Cdouble},
                         lat::AbstractVector{Cdouble},
                         lon::AbstractVector{Cdouble},
                         nmax::Integer,
                         lmax::Integer;
                         norm::Integer=1,
                         csphase::Integer=1,
                         weights::Vector{Cdouble},
                         exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::AbstractArray{Cdouble,3},
chi::Float64
```

Expand a set of irregularly sampled data points into spherical harmonics using a (weighted) least squares inversion.

See also: [`SHExpandLSQ`](@ref), [`MakeGridPoint`](@ref), [`SHExpandDH!`](@ref), [`SHExpandGLQ!`](@ref)
