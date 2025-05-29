```
p, dp = PlSchmidt_d1(lmax::Integer,
                      z::Union{AbstractFloat,Integer};
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

Compute all the Schmidt-normalized associated Legendre functions and first derivatives.

See also: [`PlSchmidt`](@ref), [`PlSchmidt_d1!`](@ref), [`PlmSchmidt_d1`](@ref), [`PlBar_d1`](@ref), [`PlON_d1`](@ref), [`PLegendre_d1`](@ref)
