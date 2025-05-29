```
get_map(map_file::String   = namad,
        map_field::Symbol  = :map_data;
        map_info::String   = splitpath(map_file)[end],
        map_units::Symbol  = :rad,
        file_units::Symbol = :deg,
        flip_map::Bool     = false)
```

保存されたHDF5またはMATファイル、またはCSVファイルを含むフォルダーからマップデータを取得します。マップは通常`:deg`単位で保存され、内部では`:rad`が使用されます。

**引数:**

  * `map_file`:   マップデータHDF5またはMATファイルのパス/名前（`.h5`または`.mat`拡張子が必要）またはCSVファイルを含むフォルダー
  * `map_field`:  （オプション）MATファイル内で使用する構造体フィールド、CSVまたはHDF5ファイルには関連しません
  * `map_info`:   （オプション）マップ情報、`map_file`にない場合のみ使用
  * `map_units`:  （オプション）`map_map`で使用するマップxx/yy単位 {`:rad`,`:deg`}
  * `file_units`: （オプション）`map_file`で使用されるマップxx/yy単位 {`:rad`,`:deg`}
  * `flip_map`:   （オプション）trueの場合、マップファイルからデータを垂直に反転します（CSVマップに便利な場合があります）

**戻り値:**

  * `map_map`: `Map` 磁気異常マップ構造体
