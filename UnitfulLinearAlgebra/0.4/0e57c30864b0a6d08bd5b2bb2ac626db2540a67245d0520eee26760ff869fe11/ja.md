```
struct UnitfulMatrix
```

`DimArray`を拡張して単位のための次元を使用し、`exact`ブールフラグも追加します。

struct UnitfulMatrix{T,N,D<:Tuple,A<:AbstractArray{T,N}} <: AbstractUnitfulVecOrMat{T,N,D,A}     data::A     dims::D     exact::Bool end
