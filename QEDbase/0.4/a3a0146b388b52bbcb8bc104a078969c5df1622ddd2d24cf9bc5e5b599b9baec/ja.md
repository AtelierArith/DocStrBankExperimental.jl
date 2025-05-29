```julia
abstract type AbstractDiracMatrix{T} <: StaticArraysCore.FieldMatrix{4, 4, T}
```

ディラック行列の抽象型、すなわちスピノル空間から別の空間への線形写像の行列表現。
