```
get_hessian(M::AbstractManifold, vgf::VectorHessianFunction, p, X, i)
get_hessian(M::AbstractManifold, vgf::VectorHessianFunction, p, X, i, range)
get_hessian!(M::AbstractManifold, X, vgf::VectorHessianFunction, p, X, i)
get_hessian!(M::AbstractManifold, X, vgf::VectorHessianFunction, p, X, i, range)
```

ベクトル関数 `vgf` のヘッセ行列を、点 `p` における多様体 `M` の方向 `X` と、指定された範囲 `range` で評価し、勾配の表現を指定します。

`i` は線形インデックスであると仮定されるため、次のように提供できます。

  * 単一の整数
  * `1:3` のように返される範囲を指定する `UnitRange`
  * 選択を指定する `BitVector`
  * インデックスを指定する `AbstractVector{<:Integer}`
  * すべてのヘッセ行列評価のベクトルを返す `:`
