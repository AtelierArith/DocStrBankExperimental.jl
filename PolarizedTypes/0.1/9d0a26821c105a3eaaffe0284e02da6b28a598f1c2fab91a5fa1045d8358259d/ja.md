```
basis_transform([T=Float64,], b1::PolBasis, b2::PolBasis)
basis_transform([T=Float64,], b1::PolBasis=>b2::PolBasis)
```

ベース `b1` からベース `b2` へのベクトル成分を変換する変換行列を生成します。つまり、例えば `E` が円形基底である場合、`basis_transform(CirBasis=>LinBasis)E` は線形基底にあります。言い換えれば、変換行列の**列**は古い基底の新しい基底ベクトルの座標ベクトルです。

# 例

```julia-repl
julia> basis_transform(CirBasis()=>LinBasis())
2×2 StaticArraysCore.SMatrix{2, 2, ComplexF64, 4} with indices SOneTo(2)×SOneTo(2):
 0.707107-0.0im       0.707107-0.0im
      0.0-0.707107im       0.0+0.707107im
```
