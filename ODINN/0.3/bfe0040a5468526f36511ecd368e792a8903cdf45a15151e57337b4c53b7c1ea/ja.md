```
function FunctionalInversion(
    model::Sleipnir.Model,
    glaciers::Vector{G},
    parameters::Sleipnir.Parameters
) where {G <: Sleipnir.AbstractGlacier}
```

氷河モデル情報、氷河、およびパラメータを持つFunctionalInversion構造体のコンストラクタ。

# 引数

  * `model::Sleipnir.Model`: シミュレーションに使用されるモデル。
  * `glaciers::Vector{G}`: シミュレーションに関与する氷河のベクトル。
  * `parameters::Sleipnir.Parameters`: シミュレーションに使用されるパラメータ。

# 戻り値

  * `FunctionalInversion`: FunctionalInversion構造体の新しいインスタンス。
