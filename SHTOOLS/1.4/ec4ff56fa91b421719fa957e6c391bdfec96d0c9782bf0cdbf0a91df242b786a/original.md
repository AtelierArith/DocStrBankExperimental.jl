```
PLegendreA_d1!(p::AbstractVector{Cdouble},
               dp::AbstractVector{Cdouble}, 
               lmax::Integer,
               z::Union{AbstractFloat,Integer};
               csphase::Integer=1,
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the unnormalized associated Legendre functions and first derivatives.

See also: [`PLegendreA_d1`](@ref), [`PLegendreA_d1`](@ref), [`PLegendre_d1!`](@ref), [`PlmBar_d1!`](@ref), [`PlmON_d1!`](@ref), [`PlmSchmidt_d1!`](@ref), [`PlmIndex`](@ref)
