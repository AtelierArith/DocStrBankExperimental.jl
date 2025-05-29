```
map_trim(map_map::Map;
         pad::Int          = 0,
         xx_lim::Tuple     = (-Inf,Inf),
         yy_lim::Tuple     = (-Inf,Inf),
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

地図データが欠落している大きな領域を削除することによって地図をトリミングします。トリミングされた磁気異常地図構造体を返します。

**引数:**

  * `map_map`:   `Map` 磁気異常地図構造体
  * `pad`:       （オプション）地図の端に沿った最小パディング（グリッドセル）
  * `xx_lim`:    （オプション）x方向の地図の制限 `(xx_min,xx_max)` [rad] または [deg] または [m]
  * `yy_lim`:    （オプション）y方向の地図の制限 `(yy_min,yy_max)` [rad] または [deg] または [m]
  * `zone_utm`:  （オプション）UTMゾーン、`map_units = :utm` の場合のみ使用
  * `is_north`:  （オプション）trueの場合、地図は北半球にあり、`map_units = :utm` の場合のみ使用
  * `map_units`: （オプション）地図のxx/yy単位 {`:rad`,`:deg`,`:utm`}
  * `silent`:    （オプション）trueの場合、出力は表示されません

**返り値:**

  * `map_map`: `Map` 磁気異常地図構造体、トリミング済み
