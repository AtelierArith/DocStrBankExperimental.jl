```
PlmSchmidt_d1!(p::AbstractVector{Cdouble},
               dp::AbstractVector{Cdouble}, 
               lmax::Integer,
               z::Union{AbstractFloat,Integer};
               csphase::Integer=1,
               cnorm::Integer=0,
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

シュミット正規化された関連レジェンドル関数とその一次導関数をすべて計算します。

参照: [`PlmSchmidt_d1`](@ref), [`PlmSchmidt_d1`](@ref), [`PlSchmidt_d1!`](@ref), [`PlmBar_d1!`](@ref), [`PlmON_d1!`](@ref), [`PLegendreA_d1!`](@ref), [`PlmIndex`](@ref)
