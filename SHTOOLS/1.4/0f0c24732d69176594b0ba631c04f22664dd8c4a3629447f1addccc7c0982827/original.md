```
cilm = SHVectorToCilm(cilm::AbstractArray{Cdouble,3},
                      vector::AbstractVector{Cdouble},
                      lmax::Integer;
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3}
```

Convert a 1-dimensional indexed vector of real spherical harmonic coefficients to a 3-dimensional array.

See also: [`SHVectorToCilm!`](@ref)
