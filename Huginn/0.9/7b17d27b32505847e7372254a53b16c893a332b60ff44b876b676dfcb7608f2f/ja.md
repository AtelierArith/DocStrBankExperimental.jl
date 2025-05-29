```
Prediction <: Simulation
```

予測シミュレーションを表す可変構造体です。

# フィールド

  * `model::Sleipnir.Model`: 予測に使用されるモデル。
  * `glaciers::Vector{Sleipnir.AbstractGlacier}`: 予測に関与する氷河のベクトル。
  * `parameters::Sleipnir.Parameters`: 予測に使用されるパラメータ。
  * `results::Vector{Results}`: 予測から得られた結果のベクトル。
