```
p, dp = PlmBar_d1(lmax::Integer,
                  z::Union{AbstractFloat,Integer};
                  csphase::Integer=1,
                  cnorm::Integer=0,
                  exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

すべての4π正規化された関連レジェンドル関数とその一次導関数を計算します。

参照してください: [`PlmBar`](@ref), [`PlmBar_d1!`](@ref), [`PlBar_d1`](@ref), [`PlmON_d1`](@ref), [`PlmSchmidt_d1`](@ref), [`PLegendreA_d1`](@ref), [`PlmIndex`](@ref)
