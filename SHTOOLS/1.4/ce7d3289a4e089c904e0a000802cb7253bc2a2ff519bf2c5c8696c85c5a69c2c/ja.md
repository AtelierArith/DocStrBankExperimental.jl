```
p = PlON(lmax::Integer,
          z::Union{AbstractFloat,Integer};
          exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
p::Vector{Cdouble}
```

すべての直交正規化された関連レジェンドル関数を計算します。

参照: [`PlON!`](@ref), [`PlON_d1`](@ref), [`PlmON`](@ref), [`PlBar`](@ref), [`PlSchmidt`](@ref), [`PLegendre`](@ref)
