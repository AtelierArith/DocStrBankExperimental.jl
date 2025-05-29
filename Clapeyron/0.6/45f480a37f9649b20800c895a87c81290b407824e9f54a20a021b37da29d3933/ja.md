```
bubble_pressure(model::EoSModel, T, x, method = ChemPotBubblePressure())
```

与えられた温度でのバブル圧力と特性を計算します。タプルを返し、以下を含みます：

  * バブル圧力 `[Pa]`
  * バブル点での液体体積 [`m³`]
  * バブル点での蒸気体積 [`m³`]
  * バブル点でのガス組成

デフォルトでは、[`ChemPotBubblePressure`](@ref)を介して化学ポテンシャルの等式を使用します。
