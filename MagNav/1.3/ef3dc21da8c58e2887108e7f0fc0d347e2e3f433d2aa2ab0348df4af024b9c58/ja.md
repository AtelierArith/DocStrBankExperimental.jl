```
map_interpolate(map_map::AbstractArray{T},
                map_xx::AbstractVector{T},
                map_yy::AbstractVector{T},
                type::Symbol = :cubic,
                map_alt::AbstractVector{T} = T[0]) where T
```

マップ補間関数を作成します。これはMATLABのgriddedInterpolantに相当します。

**引数:**

  * `map_map`: `ny` x `nx` (x `nz`) 2Dまたは3Dグリッドマップデータ
  * `map_xx`:  `nx` マップのx方向（経度）座標
  * `map_yy`:  `ny` マップのy方向（緯度）座標
  * `type`:    （オプション）補間の種類 {:linear,:quad,:cubic}
  * `map_alt`: （オプション）マップの高度レベル

**戻り値:**

  * `itp_map`: マップ補間関数 (`f(yy,xx)` または (`f(yy,xx,alt)`)
