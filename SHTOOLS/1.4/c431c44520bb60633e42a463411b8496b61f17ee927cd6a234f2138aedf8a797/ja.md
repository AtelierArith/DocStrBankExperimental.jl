```
p = PlSchmidt(lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

シュミット正規化された関連レジェンドル関数をすべて計算します。

参照: [`PlSchmidt!`](@ref), [`PlSchmidt_d1`](@ref), [`PlmSchmidt`](@ref), [`PlBar`](@ref), [`PlON`](@ref), [`PLegendre`](@ref)
