```
generate_dos(bands::Bands, kpoints::Array{KPoint, 1},
    projection::Projection;
    smear::Function=gaussian, energy_number::Integer=10000,
    ions::Array{Integer, 1}=nothing, orbits::Array{Integer, 1}=nothing)
```

バンドとk点を使用して、投影された電子状態密度を生成します。

# 引数

  * `bands::BandsWithSpin`: バンドのメタデータ
  * `kpoints::Array{KPoint, 1}`: k点のメタデータ
  * `projection::ProjectionWithSpin`: 投影のメタデータ
  * `smear::Function=gaussian`: スミアリング関数、デフォルト: ガウススミア
  * `energy_number::Integer=10000`: エネルギー点の数、デフォルト 10000
  * `ions::Union{Array{<:Integer, 1}, UnitRange{<:Integer}, Nothing}=nothing`:   波動関数が投影されるイオンのインデックス
  * `orbits::Union{Array{<:Integer, 1}, UnitRange{<:Integer}, Nothing}=nothing`:   波動関数が投影される軌道のインデックス

# 戻り値

  * `pdos1::DOS`: スピンアップの投影されたDOSのメタデータ
  * `pdos2::DOS`: スピンダウンの投影されたDOSのメタデータ
