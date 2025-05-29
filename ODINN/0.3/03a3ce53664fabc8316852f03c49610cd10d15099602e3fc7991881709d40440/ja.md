```
mutable struct FunctionalInversion <: Simulation
```

関数の逆転シミュレーションを表すオブジェクト（すなわち、データ駆動型回帰器を使用した関数の逆転）。

# フィールド

  * `model::Sleipnir.Model`: シミュレーションに使用されるモデル。
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: シミュレーションに関与する氷河のベクター。
  * `parameters::Sleipnir.Parameters`: シミュレーションに使用されるパラメータ。
  * `results::Vector{Results}`: シミュレーションの結果を格納するためのベクター。
