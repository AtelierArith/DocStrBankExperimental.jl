```
PlmBar_d1!(p::AbstractVector{Cdouble},
           dp::AbstractVector{Cdouble}, 
           lmax::Integer,
           z::Union{AbstractFloat,Integer};
           csphase::Integer=1,
           cnorm::Integer=0,
           exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the 4π-normalized associated Legendre functions and first derivatives.

See also: [`PlmBar_d1`](@ref), [`PlmBar_d1`](@ref), [`PlBar_d1!`](@ref), [`PlmON_d1!`](@ref), [`PlmSchmidt_d1!`](@ref), [`PLegendreA_d1!`](@ref), [`PlmIndex`](@ref)
