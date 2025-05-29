```
wpca(Y, i, weights=UniformWeights())
```

データ `Y` の `i` 番目の主成分を重み付きPCAを使用して計算します。すなわち、出力は重み付きサンプル共分散 `Σ_l w[l] Y[l]*Y[l]'` の `i` 番目の固有ベクトルです。データ `Y` は行列のリストです（各列がサンプルです）。

# `weights` の選択肢

  * `UniformWeights()` : 一様重み、すなわち `w[l] = 1` [デフォルト]
  * `InverseVarianceWeights([v])` : 逆ノイズ分散重み、すなわち `w[l] = 1/v[l]`
  * `OptimalWeights([v,λ])` : 分散 `λ` の信号に対する最適重み、すなわち `w[l] = 1/v[l] * 1/(1+v[l]/λ)`

`weights` は `AbstractVector{<:Real}` を渡すことで手動で設定することもできます。

参照: [`UniformWeights`](@ref), [`InverseVarianceWeights`](@ref), [`OptimalWeights`](@ref)。
