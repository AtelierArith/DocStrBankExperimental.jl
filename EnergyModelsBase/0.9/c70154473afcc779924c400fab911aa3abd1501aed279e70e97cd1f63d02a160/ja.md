```
InvestmentModel <: AbstractInvestmentModel
```

標準の [`OperationalModel`](@ref) に基づく具体的な基本投資モデルタイプです。具体的な基本投資モデルは `OperationalModel` に似ていますが、投資と将来の年の追加的な割引を許可します。

!!! note
    `EnergyModelsBase` 内で宣言されていますが、その具体的な実装は `EnergyModelsInvestments` がロードされている場合にのみアクセス可能です。


# フィールド

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** は、各排出資源 [`ResourceEmit`](@ref) に対する `TimeProfile` としての個別の排出制限を持つ辞書です。
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** は、各排出資源 [`ResourceEmit`](@ref) に対する排出コストです。
  * **`co2_instance`** は [`ResourceEmit`](@ref) であり、CO₂ に使用されるタイプに対応します。
  * **`r::Float64`** は、投資最適化における割引率です。
