```
get_x(lines, df_line::DataFrame, df_flight::DataFrame,
      features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
      features_no_norm::Vector{Symbol} = Symbol[],
      terms              = [:permanent,:induced,:eddy],
      sub_diurnal::Bool  = false,
      sub_igrf::Bool     = false,
      bpf_mag::Bool      = false,
      reorient_vec::Bool = false,
      l_window::Int      = -1,
      silent::Bool       = true)
```

複数のフライトラインから `x` データ行列を取得します。複数のフライトが含まれる可能性があります。

**引数:**

  * `lines`:   選択されたライン番号
  * `df_line`: `lines` のルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                         |
|:---------- |:-------- |:------------------------------ |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)          |
| `line`     | `Real`   | ライン番号、すなわち `flight` 内のセグメント    |
| `t_start`  | `Real`   | 使用する `line` の開始時間 [s]          |
| `t_end`    | `Real`   | 使用する `line` の終了時間 [s]          |
| `map_name` | `Symbol` | (オプション) `line` に関連する磁気異常マップの名前 |

  * `df_flight`: フライトデータファイルのルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                                               |
|:---------- |:-------- |:-------------------------------------------------------------------- |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)                                                |
| `xyz_type` | `Symbol` | フライトデータに使用する `XYZ` のサブタイプ {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}        |
| `xyz_set`  | `Real`   | フライトデータセット番号 (異なる磁力計の位置などの不適切なデータ混合を防ぐために使用)                         |
| `xyz_file` | `String` | フライトデータのCSV、HDF5、またはMATファイルのパス/名前 (`.csv`, `.h5`, または `.mat` 拡張子が必要) |

  * `features_setup`:   含める特徴のベクトル
  * `features_no_norm`: (オプション) 正規化しない特徴のベクトル
  * `terms`:            (オプション) 使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:      (オプション) true の場合、スカラー磁力計測定から日周変動を引く
  * `sub_igrf`:         (オプション) true の場合、スカラー磁力計測定からIGRFを引く
  * `bpf_mag`:          (オプション) true の場合、スカラー磁力計測定をバンドパスフィルタリング
  * `reorient_vec`:     (オプション) true の場合、ベクトル磁力計測定をボディフレームに合わせる
  * `l_window`:         (オプション) `N % l_window` でデータをトリム、`-1` は無視
  * `silent`:           (オプション) true の場合、出力なし

**戻り値:**

  * `x`:        `N` x `Nf` データ行列 (`Nf` は特徴の数)
  * `no_norm`:  正規化されない特徴の長さ-`Nf` ブールインデックス
  * `features`: 長さ-`Nf` 特徴ベクトル (TL `A` の成分を含む)
  * `l_segs`:   長さ-`N_lines` の `lines` の長さのベクトル、sum(l_segs) = `N`
