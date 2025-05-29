```
p = PlmSchmidt(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               csphase::Integer=1,
               cnorm::Integer=0,
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

シュミット正規化された関連レジェンドル関数をすべて計算します。

参照: [`PlmSchmidt!`](@ref), [`PlmSchmidt_d1`](@ref), [`PlSchmidt`](@ref), [`PlmBar`](@ref), [`PlmON`](@ref), [`PLegendreA`](@ref), [`PlmIndex`](@ref)
