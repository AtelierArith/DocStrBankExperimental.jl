```
PlON!(p::AbstractVector{Cdouble},
       lmax::Integer,
       z::Union{AbstractFloat,Integer};
       exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the orthonormalized associated Legendre functions.

See also: [`PlON`](@ref), [`PlON_d1!`](@ref), [`PlmON!`](@ref), [`PlBar!`](@ref), [`PlSchmidt!`](@ref), [`PLegendre!`](@ref)
