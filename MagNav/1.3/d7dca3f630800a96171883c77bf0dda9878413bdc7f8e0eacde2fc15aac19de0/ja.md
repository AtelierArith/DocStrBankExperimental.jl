```
get_XYZ(flight::Symbol, df_flight::DataFrame;
        tt_sort::Bool      = true,
        reorient_vec::Bool = false,
        silent::Bool       = false)
```

保存されたHDF5ファイルからDataFrameルックアップを介して`XYZ`フライトデータを取得します。

**引数:**

  * `flight`:    フライト名（例: `:Flt1001`）
  * `df_flight`: フライトデータファイルのルックアップテーブル（DataFrame）

| **フィールド**  | **型**    | **説明**                                                         |
|:---------- |:-------- |:-------------------------------------------------------------- |
| `flight`   | `Symbol` | フライト名（例: `:Flt1001`）                                           |
| `xyz_type` | `Symbol` | フライトデータに使用する`XYZ`のサブタイプ {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}    |
| `xyz_set`  | `Real`   | フライトデータセット番号（異なる磁力計の位置など、データセットの不適切な混合を防ぐために使用）                |
| `xyz_file` | `String` | フライトデータCSV、HDF5、またはMATファイルのパス/名前（`.csv`、`.h5`、または`.mat`拡張子が必要） |

  * `tt_sort`:      （オプション）trueの場合、データを時間でソートします（行ではなく）
  * `reorient_vec`: （オプション）trueの場合、ベクトル磁力計の測定値をボディフレームに合わせます
  * `silent`:       （オプション）trueの場合、出力はありません

**戻り値:**

  * `xyz`: `XYZ`フライトデータ構造体
