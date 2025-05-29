```julia
struct ContinuousQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

連続量は、正確に1つの種番号によって表されます

  * `ispec::Any`: 量を表す種番号
  * `id::Any`: パラメータフィールドでインデックスとして量を使用できるようにする量識別子
