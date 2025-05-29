```julia
toeigenbasis(
    S::Array{GF<:Keldysh.AbstractTimeGF, 1},
    ed::KeldyshED.EDCore
) -> Vector{GF} where GF<:Keldysh.AbstractTimeGF

```

フォック状態基底で書かれたブロック対角進化演算子 `S` をシステムの固有基底に変換します。
