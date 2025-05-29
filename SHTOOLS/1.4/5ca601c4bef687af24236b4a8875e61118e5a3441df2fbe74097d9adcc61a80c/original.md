```
PlBar_d1!(p::AbstractVector{Cdouble},
           dp::AbstractVector{Cdouble}, 
           lmax::Integer,
           z::Union{AbstractFloat,Integer};
           exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the 4π-normalized associated Legendre functions and first derivatives.

See also: [`PlBar_d1`](@ref), [`PlBar_d1`](@ref), [`PlmBar_d1!`](@ref), [`PlON_d1!`](@ref), [`PlSchmidt_d1!`](@ref), [`PLegendre_d1!`](@ref)
