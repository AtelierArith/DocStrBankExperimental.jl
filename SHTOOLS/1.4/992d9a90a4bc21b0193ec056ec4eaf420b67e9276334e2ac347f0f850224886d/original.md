```
PlSchmidt_d1!(p::AbstractVector{Cdouble},
               dp::AbstractVector{Cdouble}, 
               lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the Schmidt-normalized associated Legendre functions and first derivatives.

See also: [`PlSchmidt_d1`](@ref), [`PlSchmidt_d1`](@ref), [`PlmSchmidt_d1!`](@ref), [`PlBar_d1!`](@ref), [`PlON_d1!`](@ref), [`PLegendre_d1!`](@ref)
