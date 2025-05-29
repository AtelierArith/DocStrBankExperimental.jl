```
map_utm2lla(map_map::Matrix, map_xx::Vector, map_yy::Vector,
            alt, map_mask::BitMatrix;
            map_info::String = "Map",
            zone_utm::Int    = 18,
            is_north::Bool   = true,
            save_h5::Bool    = false,
            map_h5::String   = "map_data.h5")
```

`UTM` から `LLA` へのマップグリッドの変換。

**引数:**

  * `map_map`:  `ny` x `nx` の `UTM` グリッド上の 2D グリッドマップデータ
  * `map_xx`:   `nx` マップの x 方向（経度）座標 [m]
  * `map_yy`:   `ny` マップの y 方向（緯度）座標 [m]
  * `alt`:      マップの高度または高度マップ [m]
  * `map_mask`: `ny` x `nx` の有効（未入力）マップデータのマスク
  * `map_info`: （オプション）マップ情報
  * `zone_utm`: （オプション）UTM ゾーン
  * `is_north`: （オプション）true の場合、マップは北半球にある
  * `save_h5`:  （オプション）true の場合、マップデータを `map_h5` に保存
  * `map_h5`:   （オプション）保存するマップデータ HDF5 ファイルのパス/名前（`.h5` 拡張子はオプション）

**戻り値:**

  * `map_map`:  `ny` x `nx` の `LLA` グリッド上の 2D グリッドマップデータ
  * `map_xx`:   `nx` マップの x 方向（経度）座標 [rad]
  * `map_yy`:   `ny` マップの y 方向（緯度）座標 [rad]
  * `map_mask`: `ny` x `nx` の `LLA` グリッド上の有効（未入力）マップデータのマスク
