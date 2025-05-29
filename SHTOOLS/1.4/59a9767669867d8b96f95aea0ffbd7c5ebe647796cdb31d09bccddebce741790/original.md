```
vector = SHCilmToVector(cilm::AbstractArray{Cdouble,3},
                        lmax::Integer;
                        exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
vector::Vector{Cdouble}
```

Convert a three-dimensional array of real spherical harmonic coefficients to a 1-dimensional indexed array.

See also: [`SHCilmToVector!`](@ref)
