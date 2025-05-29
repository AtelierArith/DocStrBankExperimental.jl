```
p = PlmON(lmax::Integer,
          z::Union{AbstractFloat,Integer};
          csphase::Integer=1,
          cnorm::Integer=0,
          exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

Compute all the orthonormalized associated Legendre functions.

See also: [`PlmON!`](@ref), [`PlmON_d1`](@ref), [`PlON`](@ref), [`PlmBar`](@ref), [`PlmSchmidt`](@ref), [`PLegendreA`](@ref), [`PlmIndex`](@ref)
