```
to_covariance(tree::N, blv::Array{T})::Array{T,2} where {N<:AbstractNode,T<: Real}
```

`tree`から分散共分散行列を計算します。行列のエントリ (i,j) は、i と j の最新の共通祖先と木の根を結ぶパスの長さとして定義されます。

実数の配列を返します。

  * `tree` : 関心のある木のノード。
  * `blv` : 木の枝長ベクトル。
