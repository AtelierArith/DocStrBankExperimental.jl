```
p = PLegendre(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

Compute all the unnormalized associated Legendre functions.

See also: [`PLegendre!`](@ref), [`PLegendre_d1`](@ref), [`PLegendreA`](@ref), [`PlBar`](@ref), [`PlON`](@ref), [`PlSchmidt`](@ref)
