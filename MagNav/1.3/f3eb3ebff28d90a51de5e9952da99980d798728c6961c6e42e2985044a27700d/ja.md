```
save_map(map_map, map_xx, map_yy, map_alt, map_h5::String = "map_data.h5";
         map_info::String   = "Map",
         map_mask::BitArray = falses(1,1),
         map_border::Matrix = zeros(eltype(map_alt),1,1),
         map_units::Symbol  = :rad,
         file_units::Symbol = :deg)
```

地図データをHDF5ファイルに保存します。地図は通常`:deg`単位で保存されますが、内部では`:rad`が使用されます。

**引数:**

  * `map_map`:   `ny` x `nx` (x `nz`) 2Dまたは3Dグリッド地図データ
  * `map_xx`:    `nx` 地図のx方向（経度）座標 [rad] または [deg]
  * `map_yy`:    `ny` 地図のy方向（緯度）座標 [rad] または [deg]
  * `map_alt`:    地図の高度または `ny` x `nx` 2Dグリッド高度地図データ [m]
  * `map_h5`:     （オプション）保存する地図データHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `map_info`:   （オプション）地図情報
  * `map_mask`:   （オプション）有効（未入力）の地図データ用の `ny` x `nx` (x `nz`) マスク
  * `map_border`: （オプション）有効（未入力）の地図データ用の [xx yy] ボーダー [rad] または [deg]
  * `map_units`:  （オプション）`map_xx` & `map_yy` で使用される地図のxx/yy単位 {`:rad`,`:deg`}
  * `file_units`: （オプション）`map_h5` で使用する地図のxx/yy単位 {`:rad`,`:deg`}

**戻り値:**

  * `nothing`: `map_h5` が作成されます
