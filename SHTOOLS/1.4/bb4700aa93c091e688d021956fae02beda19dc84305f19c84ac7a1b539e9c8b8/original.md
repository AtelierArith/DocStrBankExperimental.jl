```
PlBar!(p::AbstractVector{Cdouble},
       lmax::Integer,
       z::Union{AbstractFloat,Integer};
       exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

Compute all the 4π-normalized Legendre polynomials.

See also: [`PlBar`](@ref), [`PlBar_d1!`](@ref), [`PlmBar!`](@ref), [`PlON!`](@ref), [`PlSchmidt!`](@ref), [`PLegendre!`](@ref)
