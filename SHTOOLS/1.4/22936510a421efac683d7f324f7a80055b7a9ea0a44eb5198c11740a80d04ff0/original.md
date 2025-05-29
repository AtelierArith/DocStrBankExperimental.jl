```
cindex = SHCilmToCindex(cilm::AbstractArray{Cdouble,3};
                        degmax::Optional{Cint}=nothing,
                        exitstatus::Optional{Ref{<:Integer}}=nothing)
cindex::Array{Cdouble,2}
```

Convert a three-dimensional array of spherical harmonic coefficients to a two-dimensional indexed array.

See also: [`SHCilmToCindex!`](@ref), [`SHCindexToCilm`](@ref), [`SHCilmToVector`](@ref)
