```julia
struct TrivialCell{D, T} <: LightLattices.AbstractCell{D, T}
```

原点に1つのノードを持つ`D`次元座標系のトリビアルセル。型`T`は座標を表すために使用されます。
