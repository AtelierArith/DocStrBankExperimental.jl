```
p, dp = PlSchmidt_d1(lmax::Integer,
                      z::Union{AbstractFloat,Integer};
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
dp::Vector{Cdouble}
```

シュミット正規化された関連レジェンドル関数とその一次導関数をすべて計算します。

参照: [`PlSchmidt`](@ref), [`PlSchmidt_d1!`](@ref), [`PlmSchmidt_d1`](@ref), [`PlBar_d1`](@ref), [`PlON_d1`](@ref), [`PLegendre_d1`](@ref)
