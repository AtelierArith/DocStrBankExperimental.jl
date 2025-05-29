```
SpatialPoint{T, D, PT} <: AbstractSpatialPoint{T, D}
```

`D`次元の空間点。

≡≡≡ フィールド ≡≡≡

`param::PT`: 空間座標の成分としての[`ParamBox`](@ref)の`Tuple`。

`marker::Symbol`: 構築された`SpatialPoint`の目的や意味を示すマーカー。デフォルトのマーカーは`:point`に設定されています。

≡≡≡ 初期化メソッド ≡≡≡

```
SpatialPoint(pbs::Union{Tuple{Quiqbox.ParamBox{T, :X, Fx}} where Fx, Tuple{Quiqbox.ParamBox{T, :X, Fx}, Quiqbox.ParamBox{T, :Y, Fy}} where {Fx, Fy}, Tuple{Quiqbox.ParamBox{T, :X, Fx}, Quiqbox.ParamBox{T, :Y, Fy}, Quiqbox.ParamBox{T, :Z, Fz}} where {Fx, Fy, Fz}} where T) -> SpatialPoint
```
