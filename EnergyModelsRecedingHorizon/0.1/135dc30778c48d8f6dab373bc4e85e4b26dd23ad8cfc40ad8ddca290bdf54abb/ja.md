```
struct RecHorOperationalModel <: RecHorEnergyModel
```

投資なしの運用エネルギーモデル、後退ホライズン実装。

# フィールド

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** は、各排出資源 `ResourceEmit` のための `TimeProfile` としての個別の排出制限を持つ辞書です。
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** は、考慮される異なる排出タイプの価格です。
  * **`co2_instance`** は `ResourceEmit` であり、CO₂ に使用されるタイプに対応します。
