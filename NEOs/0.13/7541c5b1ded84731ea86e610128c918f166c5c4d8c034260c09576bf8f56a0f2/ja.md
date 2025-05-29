```
obsposECEF(observatory::ObservatoryMPC{T}; kwarg) where {T <: AbstractFloat}
obsposECEF(x::RadecMPC{T}; kwarg) where {T <: AbstractFloat}
obsposECEF(x::RadarJPL{T}; kwarg) where {T <: AbstractFloat}
```

観測者の地心の `[x, y, z]` 位置ベクトルを地球中心地球固定 (ECEF) 参照フレームで返します。

# キーワード引数

  * `eop::Union{EopIau1980, EopIau2000A}`: 地球の姿勢パラメータ (eop)。
