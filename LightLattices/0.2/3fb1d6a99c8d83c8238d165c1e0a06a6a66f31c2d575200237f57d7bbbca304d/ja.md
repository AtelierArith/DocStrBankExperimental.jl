```julia
abstract type AbstractCell{D, T} <: LightLattices.AbstractNodeCollection{D, T}
```

`D`次元空間におけるノードの抽象的な無秩序コレクション。型 `T` は座標を表すために使用されます。
