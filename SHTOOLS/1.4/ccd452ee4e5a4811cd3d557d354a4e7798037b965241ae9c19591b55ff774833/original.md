```
SHCilmToVector!(vector::AbstractVector{Cdouble},
                cilm::AbstractArray{Cdouble,3},
                lmax::Integer;
                exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Convert a three-dimensional array of real spherical harmonic coefficients to a 1-dimensional indexed vector.

See also: [`SHCilmToVector`](@ref)
