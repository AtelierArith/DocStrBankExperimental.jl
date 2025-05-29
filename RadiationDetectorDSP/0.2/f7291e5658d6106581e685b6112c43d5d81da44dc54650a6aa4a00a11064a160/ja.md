```
struct SavitzkyGolayFilter <: AbstractRadFIRFilter
```

[Aサヴィッツキー・ゴレー滤波器](https://en.wikipedia.org/wiki/Savitzky%E2%80%93Golay_filter)。

コンストラクタ:

  * `SavitzkyGolayFilter(; fields...)`

フィールド:

  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルターの長さ
  * `degree::Int64`: 多項式の次数
  * `derivative::Int64`: n階導関数 (導関数なしの場合は0)
