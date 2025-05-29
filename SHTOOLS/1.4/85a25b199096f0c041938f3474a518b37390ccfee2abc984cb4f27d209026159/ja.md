```
p = PLegendreA(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               csphase::Integer=1,
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

すべての正規化されていない関連レジェンドル関数を計算します。

参照: [`PLegendreA!`](@ref), [`PLegendreA_d1`](@ref), [`PLegendre`](@ref), [`PlmBar`](@ref), [`PlmON`](@ref), [`PlmSchmidt`](@ref), [`PlmIndex`](@ref)
