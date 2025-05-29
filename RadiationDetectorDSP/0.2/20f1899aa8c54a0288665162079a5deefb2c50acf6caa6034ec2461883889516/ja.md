```
struct Intersect <: Function
```

Yと閾値の交差点を見つけます

コンストラクタ:

  * `Intersect(; fields...)`

フィールド:

  * `mintot::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 最小時間超過閾値
