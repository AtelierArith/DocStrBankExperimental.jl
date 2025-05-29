```
p = PlSchmidt(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

Compute all the Schmidt-normalized associated Legendre functions.

See also: [`PlSchmidt!`](@ref), [`PlSchmidt_d1`](@ref), [`PlmSchmidt`](@ref), [`PlBar`](@ref), [`PlON`](@ref), [`PLegendre`](@ref)
