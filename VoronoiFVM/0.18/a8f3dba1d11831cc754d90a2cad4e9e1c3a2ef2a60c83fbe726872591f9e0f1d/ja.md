```julia
struct DiscontinuousQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

不連続量は隣接する領域で異なる種によって表されます。

  * `regionspec::Vector`: 各領域における量を表す種の番号
  * `id::Any`: パラメータフィールドでインデックスとして量を使用できるようにする量の識別子
