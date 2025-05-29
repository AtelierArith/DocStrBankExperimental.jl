```
bubble_temperature(model::EoSModel, p, x,method::BubblePointMethod = ChemPotBubbleTemperature())
```

与えられた圧力でのバブル温度と特性を計算します。次の内容を含むタプルを返します：

  * バブル温度 `[K]`
  * バブルポイントでの液体体積 [`m³`]
  * バブルポイントでの蒸気体積 [`m³`]
  * バブルポイントでのガス組成

デフォルトでは、[`ChemPotBubbleTemperature`](@ref)を介して化学ポテンシャルの等式を使用します。
