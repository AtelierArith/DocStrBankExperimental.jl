```
get_y(lines, df_line::DataFrame, df_flight::DataFrame,
      df_map::DataFrame;
      y_type::Symbol    = :d,
      use_mag::Symbol   = :mag_1_uc,
      use_mag_c::Symbol = :mag_1_c,
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false,
      l_window::Int     = -1,
      silent::Bool      = true)
```

複数のフライトラインから `y` ターゲットベクトルを取得します。複数のフライトが含まれる可能性があります。

**引数:**

  * `lines`:   選択されたライン番号
  * `df_line`: `lines` のルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                                   |
|:---------- |:-------- |:-------------------------------------------------------- |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)                                    |
| `line`     | `Real`   | ライン番号、すなわち `flight` 内のセグメント                              |
| `t_start`  | `Real`   | 使用する `line` の開始時間 [s]                                    |
| `t_end`    | `Real`   | 使用する `line` の終了時間 [s]                                    |
| `map_name` | `Symbol` | (オプション) `line` に関連する磁気異常マップの名前、`y_type = :b, :c` の場合のみ使用 |

  * `df_flight`: フライトデータファイルのルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                                           |
|:---------- |:-------- |:---------------------------------------------------------------- |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)                                            |
| `xyz_type` | `Symbol` | フライトデータに使用する `XYZ` のサブタイプ {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}    |
| `xyz_set`  | `Real`   | フライトデータセット番号 (異なる磁力計の位置など、データセットの不適切な混合を防ぐために使用)                 |
| `xyz_file` | `String` | フライトデータのCSV、HDF5、またはMATファイルのパス/名前 (`.csv`、`.h5`、または`.mat`拡張子が必要) |

  * `df_map`: マップデータファイルのルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                             |
|:---------- |:-------- |:-------------------------------------------------- |
| `map_name` | `Symbol` | 磁気異常マップの名前                                         |
| `map_file` | `String` | マップデータのHDF5またはMATファイルのパス/名前 (`.h5`または`.mat`拡張子が必要) |

  * `y_type`: (オプション) `y` ターゲットタイプ

      * `:a` = 異常場 #1、補償されたテールスティンガーのトータルフィールドスカラー磁力計測定値
      * `:b` = 異常場 #2、補間された `磁気異常マップ` の値
      * `:c` = 航空機場 #1、補償されていないキャビンのトータルフィールドスカラー磁力計測定値と補間された `磁気異常マップ` の値の差
      * `:d` = 航空機場 #2、補償されていないキャビンと補償されたテールスティンガーのトータルフィールドスカラー磁力計測定値の差
      * `:e` = BPF'd トータルフィールド、バンドパスフィルタされた補償されていないキャビンのトータルフィールドスカラー磁力計測定値
  * `use_mag`:     (オプション) `y` ターゲットベクトルに使用する補償されていないスカラー磁力計 {`:mag_1_uc` など}、`y_type = :c, :d, :e` の場合のみ使用
  * `use_mag_c`:   (オプション) `y` ターゲットベクトルに使用する補償されたスカラー磁力計 {`:mag_1_c` など}、`y_type = :a, :d` の場合のみ使用
  * `sub_diurnal`: (オプション) true の場合、スカラー磁力計測定値から日変化を引く
  * `sub_igrf`:    (オプション) true の場合、スカラー磁力計測定値からIGRFを引く
  * `l_window`:    (オプション) `N % l_window` でデータをトリム、`-1` は無視
  * `silent`:      (オプション) true の場合、出力を表示しない

**戻り値:**

  * `y`: 長さ `N` のターゲットベクトル

```
