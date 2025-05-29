```
cilm = SHCindexToCilm!(cilm::AbstractArray{Cdouble,3},
                       cindex::AbstractArray{Cdouble,2};
                       degmax::Optional{Cint}=nothing,
                       exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::AbstractArray{Cdouble,3},
```

Convert a two-dimensional indexed array of spherical harmonic coefficients to a three-dimensional array.

See also: [`SHCindexToCilm`](@ref), [`SHCilmToCindex!`](@ref), [`SHVectorToCilm!`](@ref)
