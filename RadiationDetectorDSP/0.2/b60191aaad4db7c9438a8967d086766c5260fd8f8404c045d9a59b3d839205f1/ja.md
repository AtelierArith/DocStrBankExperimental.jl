```
struct TruncateFilter <: AbstractRadSigFilter{LinearFiltering}
```

入力信号を切り捨てるフィルター。

コンストラクタ:

  * `TruncateFilter(; fields...)`

フィールド:

  * `interval::IntervalSets.ClosedInterval{<:Union{Real, Unitful.AbstractQuantity{<:Real}}}`: 保持する区間
