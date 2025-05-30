```julia
struct InterfaceQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

インターフェース量は、正確に1つの種番号によって表されます

  * `ispec::Any`: 量を表す種番号
  * `bregspec::Vector`: インターフェース量が定義されている境界領域
  * `id::Any`: パラメータフィールドでインデックスとして量を使用することを可能にする量識別子
