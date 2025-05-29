```
Inversion <: Simulation
```

反転シミュレーションを表す可変構造体です。

# フィールド

  * `model::Sleipnir.Model`: 反転に使用されるモデル。
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: 反転に関与する氷河のベクター。
  * `parameters::Sleipnir.Parameters`: 反転に使用されるパラメータ。
  * `inversion::Vector{InversionResults}`: 反転からの結果のベクター。
