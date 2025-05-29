```
p = PlmBar(lmax::Integer,
           z::Union{AbstractFloat,Integer};
           csphase::Integer=1,
           cnorm::Integer=0,
           exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

すべての4π正規化された関連レジェンドル関数を計算します。

参照: [`PlmBar!`](@ref), [`PlmBar_d1`](@ref), [`PlBar`](@ref), [`PlmON`](@ref), [`PlmSchmidt`](@ref), [`PLegendreA`](@ref), [`PlmIndex`](@ref)
