```
p = PlBar(lmax::Integer,
           z::Union{AbstractFloat,Integer};
           exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

Compute all the 4π-normalized associated Legendre functions.

See also: [`PlBar!`](@ref), [`PlBar_d1`](@ref), [`PlmBar`](@ref), [`PlON`](@ref), [`PlSchmidt`](@ref), [`PLegendre`](@ref)
