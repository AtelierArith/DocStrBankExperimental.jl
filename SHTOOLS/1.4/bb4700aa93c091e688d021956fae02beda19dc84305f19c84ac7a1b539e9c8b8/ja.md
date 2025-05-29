```
PlBar!(p::AbstractVector{Cdouble},
       lmax::Integer,
       z::Union{AbstractFloat,Integer};
       exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

すべての4π正規化されたレジェンドル多項式を計算します。

参照: [`PlBar`](@ref), [`PlBar_d1!`](@ref), [`PlmBar!`](@ref), [`PlON!`](@ref), [`PlSchmidt!`](@ref), [`PLegendre!`](@ref)
