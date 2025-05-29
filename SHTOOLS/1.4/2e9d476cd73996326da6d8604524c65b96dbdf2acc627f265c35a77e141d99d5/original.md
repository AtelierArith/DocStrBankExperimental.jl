```
p = PlmBar(lmax::Integer,
           z::Union{AbstractFloat,Integer};
           csphase::Integer=1,
           cnorm::Integer=0,
           exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

Compute all the 4π-normalized associated Legendre functions.

See also: [`PlmBar!`](@ref), [`PlmBar_d1`](@ref), [`PlBar`](@ref), [`PlmON`](@ref), [`PlmSchmidt`](@ref), [`PLegendreA`](@ref), [`PlmIndex`](@ref)
