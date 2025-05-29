```
p, dp = PlBar_d1(lmax::Integer,
                  z::Union{AbstractFloat,Integer};
                  exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

すべての4π正規化された関連レジェンドル関数とその一次導関数を計算します。

参照: [`PlBar`](@ref), [`PlBar_d1!`](@ref), [`PlmBar_d1`](@ref), [`PlON_d1`](@ref), [`PlSchmidt_d1`](@ref), [`PLegendre_d1`](@ref)
