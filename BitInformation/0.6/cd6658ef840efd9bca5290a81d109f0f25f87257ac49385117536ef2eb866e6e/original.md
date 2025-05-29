```julia
B = biased_exponent(A::AbstractArray{T}) where {T<:Base.IEEEFloat}
```

Convert the signed exponents from `signed_exponent` back into the  standard biased exponents of IEEE floats.
