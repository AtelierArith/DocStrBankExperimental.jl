```
PlmSchmidt!(p::AbstractVector{Cdouble},
            lmax::Integer,
            z::Union{AbstractFloat,Integer};
            csphase::Integer=1,
            cnorm::Integer=0,
            exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the Schmidt-normalized associated Legendre functions.

See also: [`PlmSchmidt`](@ref), [`PlmSchmidt_d1!`](@ref), [`PlSchmidt!`](@ref), [`PlmBar!`](@ref), [`PlmON!`](@ref), [`PLegendreA!`](@ref), [`PlmIndex`](@ref)
