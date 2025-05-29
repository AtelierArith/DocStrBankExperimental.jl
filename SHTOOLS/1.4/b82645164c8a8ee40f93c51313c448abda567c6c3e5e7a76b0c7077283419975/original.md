```
cilm, chi = SHExpandLSQ(d::AbstractVector{Cdouble},
                        lat::AbstractVector{Cdouble},
                        lon::AbstractVector{Cdouble},
                        nmax::Integer,
                        lmax::Integer;
                        norm::Integer=1,
                        csphase::Integer=1,
                        weights::Vector{Cdouble},
                        exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3},
chi::Cdouble
```

Expand a set of irregularly sampled data points into spherical harmonics using a (weighted) least squares inversion.

See also: [`SHExpandLSQ!`](@ref), [`MakeGridPoint`](@ref), [`SHExpandDH`](@ref), [`SHExpandGLQ`](@ref)
