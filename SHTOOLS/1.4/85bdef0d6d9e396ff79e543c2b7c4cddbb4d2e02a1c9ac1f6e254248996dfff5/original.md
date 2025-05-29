```
p, dp = PlON_d1(lmax::Integer,
                 z::Union{AbstractFloat,Integer};
                 exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

Compute all the orthonormalized associated Legendre functions and first derivatives.

See also: [`PlON`](@ref), [`PlON_d1!`](@ref), [`PlmON_d1`](@ref), [`PlBar_d1`](@ref), [`PlSchmidt_d1`](@ref), [`PLegendre_d1`](@ref)
