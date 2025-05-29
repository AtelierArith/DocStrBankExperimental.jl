```
save_map(map_map::Map, map_h5::String = "map_data.h5";
         map_border::Matrix = zeros(eltype(map_map.alt),1,1),
         map_units::Symbol  = :rad,
         file_units::Symbol = :deg)
```

HDF5ファイルにマップデータを保存します。マップは通常`:deg`単位で保存されますが、内部では`:rad`が使用されます。

**引数:**

  * `map_map`:    `Map` 磁気異常マップ構造体
  * `map_h5`:     (オプション) 保存するマップデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `map_border`: (オプション) 有効な（埋められていない）マップデータのための[xx yy]境界 [rad]または[deg]
  * `map_units`:  (オプション) `map_map`で使用されるマップxx/yy単位 {`:rad`,`:deg`}
  * `file_units`: (オプション) `map_h5`で使用するマップxx/yy単位 {`:rad`,`:deg`}

**戻り値:**

  * `nothing`: `map_h5`が作成されます
