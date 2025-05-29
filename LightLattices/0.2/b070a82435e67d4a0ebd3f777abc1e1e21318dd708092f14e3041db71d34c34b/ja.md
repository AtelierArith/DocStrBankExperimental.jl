```julia
abstract type AbstractLattice{D, T, PB} <: LightLattices.AbstractNodeCollection{D, T}
```

`D`次元空間における格子のスーパタイプ。型`T`は座標を表すために使用されます。境界条件は周期的（`PB=true`）または自由（`PB=false`）のいずれかです。
