```
p, dp = PlmBar_d1(lmax::Integer,
                  z::Union{AbstractFloat,Integer};
                  csphase::Integer=1,
                  cnorm::Integer=0,
                  exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

Compute all the 4π-normalized associated Legendre functions and first derivatives.

See also: [`PlmBar`](@ref), [`PlmBar_d1!`](@ref), [`PlBar_d1`](@ref), [`PlmON_d1`](@ref), [`PlmSchmidt_d1`](@ref), [`PLegendreA_d1`](@ref), [`PlmIndex`](@ref)
