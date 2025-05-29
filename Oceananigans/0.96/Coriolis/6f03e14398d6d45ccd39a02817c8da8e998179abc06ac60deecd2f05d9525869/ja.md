```
HydrostaticSphericalCoriolis([FT=Float64;]
                             rotation_rate = Ω_Earth,
                             scheme = EnstrophyConserving())
```

回転率 `rotation_rate` で回転する球体上のコリオリ力のためのパラメータオブジェクトを返します。

# キーワード引数

  * `rotation_rate`: 球体の回転率; デフォルト: [`Ω_Earth`](@ref).
  * `scheme`: `EnergyConserving()`, `EnstrophyConserving()`, または `EnstrophyConserving()` のいずれか (デフォルト)。
