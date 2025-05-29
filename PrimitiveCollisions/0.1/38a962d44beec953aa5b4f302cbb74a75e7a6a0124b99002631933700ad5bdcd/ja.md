```julia
abstract type AbstractPolygon{D} <: AbstractShape{D} end
```

`D`次元のすべての多角形のための抽象スーパタイプ。非多角形は球体などである可能性があります。
