```
`Inversion(model::Sleipnir.Model, glaciers::Vector{G}, parameters::Sleipnir.Parameters) where {G <: Sleipnir.AbstractGlacier}`

提供されたモデル、氷河、およびパラメータを使用して`Inversion`オブジェクトを作成します。

# 引数

  * `model::Sleipnir.Model`: 反転に使用されるモデル。
  * `glaciers::Vector{G}`: 各氷河が`Sleipnir.AbstractGlacier`のサブタイプである氷河のベクター。
  * `parameters::Sleipnir.Parameters`: 反転に使用されるパラメータ。

# 戻り値

  * `inversion`: 提供されたモデル、氷河、およびパラメータで初期化された`Inversion`オブジェクト。
```
