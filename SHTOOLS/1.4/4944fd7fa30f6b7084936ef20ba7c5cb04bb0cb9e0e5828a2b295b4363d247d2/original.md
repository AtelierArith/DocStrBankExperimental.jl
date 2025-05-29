```
SHVectorToCilm!(cilm::AbstractArray{Cdouble,3},
                vector::AbstractVector{Cdouble},
                lmax::Integer;
                exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Convert a 1-dimensional indexed vector of real spherical harmonic coefficients to a 3-dimensional array.

See also: [`SHVectorToCilm`](@ref)
