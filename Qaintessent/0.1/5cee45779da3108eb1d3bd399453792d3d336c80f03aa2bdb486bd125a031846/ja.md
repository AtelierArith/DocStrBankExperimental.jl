```
apply(ψ::Vector{<:Complex}, c::Circuit{N}) where {N}
```

は、状態ベクトル `ψ` に対して `c.cgc` の回路ゲートを適用した後、`c.meas` の測定演算子からの期待値のリストを返します。
