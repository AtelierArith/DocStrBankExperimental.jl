```julia
abstract type AbstractDiracVector{T} <: StaticArraysCore.FieldVector{4, T}
```

ディラックベクトルの抽象型、例えばスピノル空間からの四次元ベクトル。
