```
get_map(map_name::Symbol, df_map::DataFrame,
        map_field::Symbol  = :map_data;
        map_info::String   = "$map_name",
        map_units::Symbol  = :rad,
        file_units::Symbol = :deg,
        flip_map::Bool     = false)
```

保存されたHDF5またはMATファイル、またはCSVファイルを含むフォルダーからDataFrameルックアップを介してマップデータを取得します。マップは通常`:deg`単位で保存され、内部では`:rad`が使用されます。

**引数:**

  * `map_name`: 磁気異常マップの名前
  * `df_map`:   マップデータHDF5および/またはMATファイルおよび/またはCSVファイルを含むフォルダーのルックアップテーブル（DataFrame）

| **フィールド**  | **型**    | **説明**                                                             |
|:---------- |:-------- |:------------------------------------------------------------------ |
| `map_name` | `Symbol` | 磁気異常マップの名前                                                         |
| `map_file` | `String` | マップデータHDF5またはMATファイルのパス/名前（`.h5`または`.mat`拡張子が必要）またはCSVファイルを含むフォルダー |

  * `map_info`:   （オプション）マップ情報、`map_file`にない場合のみ使用
  * `map_field`:  （オプション）使用するMATファイル内の構造体フィールド、CSVまたはHDF5ファイルには関連しない
  * `map_units`:  （オプション）`map_map`で使用するマップxx/yy単位 {`:rad`,`:deg`}
  * `file_units`: （オプション）`df_map`内のファイルで使用されるマップxx/yy単位 {`:rad`,`:deg`}
  * `flip_map`:   （オプション）trueの場合、マップファイルからデータを垂直に反転（CSVマップに便利な場合があります）

**戻り値:**

  * `map_map`: `Map` 磁気異常マップ構造体
