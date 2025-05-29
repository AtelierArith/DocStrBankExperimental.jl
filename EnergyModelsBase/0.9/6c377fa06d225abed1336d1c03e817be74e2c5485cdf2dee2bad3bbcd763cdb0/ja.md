```
OperationalModel <: EnergyModel
```

投資なしの運用エネルギーモデル。

# フィールド

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** は、各排出資源 [`ResourceEmit`](@ref) のための `TimeProfile` としての個別の排出制限を持つ辞書です。
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** は、各排出資源 [`ResourceEmit`](@ref) のための排出コストです。
  * **`co2_instance`** は [`ResourceEmit`](@ref) であり、CO₂ に使用されるタイプに対応します。
