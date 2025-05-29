```
PLegendreA!(p::AbstractVector{Cdouble},
            lmax::Integer,
            z::Union{AbstractFloat,Integer};
            csphase::Integer=1,
            exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the unnormalized associated Legendre functions.

See also: [`PLegendreA`](@ref), [`PLegendreA_d1!`](@ref), [`PLegendre!`](@ref), [`PlmBar!`](@ref), [`PlmON!`](@ref), [`PlmSchmidt!`](@ref), [`PlmIndex`](@ref)
