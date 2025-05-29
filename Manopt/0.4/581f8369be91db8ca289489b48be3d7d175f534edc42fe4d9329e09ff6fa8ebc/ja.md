```
get_gradient(M::AbstractManifold, vgf::VectorGradientFunction, p, i)
get_gradient(M::AbstractManifold, vgf::VectorGradientFunction, p, i, range)
get_gradient!(M::AbstractManifold, X, vgf::VectorGradientFunction, p, i)
get_gradient!(M::AbstractManifold, X, vgf::VectorGradientFunction, p, i, range)
```

ベクトル関数 `vgf` の勾配を多様体 `M` の点 `p` で評価し、`range` で指定された値を使用して勾配の表現を指定します。

`i` は線形インデックスであると仮定されるため、次のように提供できます。

  * 単一の整数
  * `1:3` のように返される範囲を指定する `UnitRange`
  * 選択を指定する `BitVector`
  * インデックスを指定する `AbstractVector{<:Integer}`
  * すべての勾配のベクトルを返す `:`
