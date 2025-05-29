```
predictedfn(param, data::RNAData, model::AbstractGeneTransitionModel)
```

単一のRNAヒストグラムの尤度を計算します。

# 引数

  * `param`: モデルのパラメータ。
  * `data::RNAData`: RNAデータ。
  * `model::AbstractGeneTransitionModel`: モデル。

# 戻り値

  * `Vector{Float64}`: RNAヒストグラムの定常状態確率。
