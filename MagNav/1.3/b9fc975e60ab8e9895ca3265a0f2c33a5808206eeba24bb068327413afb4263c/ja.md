```
get_ind(xyz::XYZ, line::Real, df_line::DataFrame;
        splits        = (1),
        l_window::Int = -1)
```

データフレームのルックアップを介してさらなる分析のためのインデックスの BitVector を取得します。

**引数:**

  * `xyz`:     `XYZ` フライトデータ構造
  * `line`:    行番号
  * `df_line`: `lines` のルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                         |
|:---------- |:-------- |:------------------------------ |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)          |
| `line`     | `Real`   | 行番号、すなわち `flight` 内のセグメント      |
| `t_start`  | `Real`   | 使用する `line` の開始時間 [s]          |
| `t_end`    | `Real`   | 使用する `line` の終了時間 [s]          |
| `map_name` | `Symbol` | (オプション) `line` に関連する磁気異常マップの名前 |

  * `splits`:   (オプション) データの分割、合計は 1 でなければならない
  * `l_window`: (オプション) `N % l_window` によってデータをトリム、`-1` は無視する

**戻り値:**

  * `ind`: 選択されたデータインデックスの BitVector (または BitVector のタプル)
