```
Prediction(model::Sleipnir.Model, glaciers::Vector{G}, parameters::Sleipnir.Parameters) where {G <: Sleipnir.AbstractGlacier}
```

与えられたモデル、氷河、およびパラメータを使用して `Prediction` オブジェクトを作成します。

# 引数

  * `model::Sleipnir.Model`: 予測に使用されるモデル。
  * `glaciers::Vector{G}`: 各氷河が `Sleipnir.AbstractGlacier` のサブタイプである氷河オブジェクトのベクター。
  * `parameters::Sleipnir.Parameters`: 予測に使用されるパラメータ。

# 戻り値

  * `Prediction`: 入力値に基づいた `Prediction` オブジェクト。
