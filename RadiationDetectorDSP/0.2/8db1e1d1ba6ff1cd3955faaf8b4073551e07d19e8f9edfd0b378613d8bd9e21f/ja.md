```
struct TrapezoidalChargeFilter <: AbstractRadNonlinearFilter
```

ステップ信号に応答する台形パルスのフィルターです。

このフィルターは、ギャップで分離された2つの移動平均に相当します。

コンストラクタ:

  * `TrapezoidalChargeFilter(; fields...)`

フィールド:

  * `avgtime::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 上昇前の平均時間
  * `gaptime::Union{Real, Unitful.AbstractQuantity{<:Real}}`: ギャップ時間
  * `avgtime2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 上昇後の平均時間

入力の急激なステップは、上昇時間と下降時間が `avgtime` で、長さが `gaptime` の平坦なトップを持つ台形を生成します。
