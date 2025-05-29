```
obsposvelECI(observatory::ObservatoryMPC{T}, et::U; kwarg) where {T <: AbstractFloat, U <: Number}
obsposvelECI(x::RadecMPC{T}; kwarg) where {T <: AbstractFloat}
obsposvelECI(x::RadarJPL{T}; kwarg) where {T <: AbstractFloat}
```

地球中心の慣性 (ECI) 参照フレームにおける観測者の地心 `[x, y, z, v_x, v_y, v_z]` "状態" ベクトルを返します。デフォルトでは、IAU200A 地球方向モデルが使用され、地球中心、地球固定 (ECEF) フレームから ECI フレームへの変換が行われます。IAU1976/80 モデルなどの他の地球方向モデルは、`SatelliteToolboxTransformations.EopIau1980` 型をインポートし、関数呼び出しの `eop` キーワード引数に渡すことで使用できます。

また、[`SatelliteToolboxBase.OrbitStateVector`](@ref) および [`SatelliteToolboxTransformations.sv_ecef_to_eci`](@ref) も参照してください。

# 引数

  * `observatory::ObservatoryMPC{T}`: 観測地点。
  * `et::U`: エフェメリス時間 (J2000.0 紀元からの TDB 秒)。
  * `x::RadecMPC{T}/RadarJPL{T}`: 天体観測。

# キーワード引数

  * `eop::Union{EopIau1980, EopIau2000A}`: 地球方向パラメータ (eop)。
