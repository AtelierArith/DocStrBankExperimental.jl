```
p = PLegendre(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

すべての非正規化された関連レジェンドル関数を計算します。

参照: [`PLegendre!`](@ref), [`PLegendre_d1`](@ref), [`PLegendreA`](@ref), [`PlBar`](@ref), [`PlON`](@ref), [`PlSchmidt`](@ref)
