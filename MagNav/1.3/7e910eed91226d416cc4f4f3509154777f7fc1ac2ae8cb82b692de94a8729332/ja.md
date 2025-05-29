```
map_trim(map_map::Matrix,
         map_xx::Vector    = collect(axes(map_map,2)),
         map_yy::Vector    = collect(axes(map_map,1)),
         pad::Int          = 0,
         xx_lim::Tuple     = (-Inf,Inf),
         yy_lim::Tuple     = (-Inf,Inf),
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

大きな地図データが欠落している領域を削除することによって地図をトリミングします。適切にトリミングされた地図を生成する元の地図のインデックスを返します。

**引数:**

  * `map_map`:   `ny` x `nx` 2D グリッド地図データ
  * `map_xx`:    (オプション) `nx` 地図の x 方向（経度）座標 [rad] または [deg] または [m]
  * `map_yy`:    (オプション) `ny` 地図の y 方向（緯度）座標 [rad] または [deg] または [m]
  * `pad`:       (オプション) 地図の端に沿った最小パディング（グリッドセル）
  * `xx_lim`:    (オプション) x 方向の地図の制限 `(xx_min,xx_max)` [rad] または [deg] または [m]
  * `yy_lim`:    (オプション) y 方向の地図の制限 `(yy_min,yy_max)` [rad] または [deg] または [m]
  * `zone_utm`:  (オプション) UTM ゾーン、`map_units = :utm` の場合のみ使用
  * `is_north`:  (オプション) true の場合、地図は北半球にあり、`map_units = :utm` の場合のみ使用
  * `map_units`: (オプション) 地図の xx/yy 単位 {`:rad`,`:deg`,`:utm`}
  * `silent`:    (オプション) true の場合、出力なし

**返り値:**

  * `ind_xx`: `nx` トリミングされた x 方向の地図インデックス
  * `ind_yy`: `ny` トリミングされた y 方向の地図インデックス
