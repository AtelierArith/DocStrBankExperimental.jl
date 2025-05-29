```
predictedfn(param, data::AbstractHistogramData, model::AbstractGeneTransitionModel)
```

複数のヒストグラムの尤度を計算します。

# 引数

  * `param`: モデルのパラメータ。
  * `data::AbstractHistogramData`: ヒストグラムデータ。
  * `model::AbstractGeneTransitionModel`: モデル。

# 戻り値

  * `Array{Float64,2}`: ヒストグラムの尤度の配列。
