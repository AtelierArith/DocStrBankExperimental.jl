```
sgp4!(sgp4d::Sgp4Propagator{Tepoch, T}, t::Number) where T
```

`sgp4d`で定義された軌道を時間`t` [分]まで伝播させます（[`Sgp4Propagator`](@ref）を参照）。

!!! note
    `sgp4d`内の値は変更されます。


# 戻り値

  * `SVector{T, 3}`: 時間`t` [km]におけるTEMEフレームで表された位置ベクトル。
  * `SVector{T, 3}`: 時間`t` [km/s]におけるTEMEフレームで表された速度ベクトル。
