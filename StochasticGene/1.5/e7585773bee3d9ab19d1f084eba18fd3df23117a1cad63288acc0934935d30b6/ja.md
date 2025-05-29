```
predictedarray(r, data::RNAOnOffData, model::AbstractGeneTransitionModel)
```

RNA On/Offデータの尤度を計算します。

# 引数

  * `r`: レート。
  * `data::RNAOnOffData`: RNA On/Offデータ。
  * `model::AbstractGeneTransitionModel`: モデル。

# 戻り値

  * `Array{Float64,1}`: RNA On/Offデータの尤度。
