```julia
tofockbasis(
    S::Array{GF<:Keldysh.AbstractTimeGF, 1},
    ed::KeldyshED.EDCore
) -> Vector{GF} where GF<:Keldysh.AbstractTimeGF

```

ブロック対角進化演算子 `S` をシステムの固有基底で書かれたものからフォック状態基底に変換します。
