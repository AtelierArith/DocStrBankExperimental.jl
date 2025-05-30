```julia
abstract type AbstractLorentzVector{T} <: StaticArraysCore.FieldVector{4, T}
```

一般的なローレンツベクトルをモデル化するための抽象型、すなわちミンコフスキー様空間の要素であり、コンポーネント空間は任意です。
