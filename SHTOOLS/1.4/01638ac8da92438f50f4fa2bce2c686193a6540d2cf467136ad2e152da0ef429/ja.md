```
p, dp = PLegendreA_d1(lmax::Integer,
                        z::Union{AbstractFloat,Integer};
                        csphase::Integer=1,
                        exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

すべての非正規化された関連レジェンドル関数とその一次導関数を計算します。

参照: [`PLegendreA`](@ref), [`PLegendreA_d1!`](@ref), [`PLegendre_d1`](@ref), [`PlmBar_d1`](@ref), [`PlmON_d1`](@ref), [`PlmSchmidt_d1`](@ref), [`PlmIndex`](@ref)
