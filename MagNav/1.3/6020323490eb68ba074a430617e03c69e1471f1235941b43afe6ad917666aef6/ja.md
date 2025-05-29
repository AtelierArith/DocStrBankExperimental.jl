```
get_Axy(lines, df_line::DataFrame,
        df_flight::DataFrame, df_map::DataFrame,
        features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
        features_no_norm::Vector{Symbol} = Symbol[],
        y_type::Symbol     = :d,
        use_mag::Symbol    = :mag_1_uc,
        use_mag_c::Symbol  = :mag_1_c,
        use_vec::Symbol    = :flux_a,
        terms              = [:permanent,:induced,:eddy],
        terms_A            = [:permanent,:induced,:eddy,:bias],
        sub_diurnal::Bool  = false,
        sub_igrf::Bool     = false,
        bpf_mag::Bool      = false,
        reorient_vec::Bool = false,
        l_window::Int      = -1,
        mod_TL::Bool       = false,
        map_TL::Bool       = false,
        return_B::Bool     = false,
        silent::Bool       = true)
```

外部トレス・ローソン `A` 行列、`x` データ行列、および複数のフライトラインからの `y` ターゲットベクトルを取得します。複数のフライトを含む可能性があります。オプションで、外部トレス・ローソン `A` 行列を作成するために使用される `Bt` および `B_dot` を返します。

**引数:**

  * `lines`:   選択されたライン番号
  * `df_line`: `lines` のルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                                       |
|:---------- |:-------- |:------------------------------------------------------------ |
| `flight`   | `Symbol` | フライト名 (例: `:Flt1001`)                                        |
| `line`     | `Real`   | ライン番号、すなわち `flight` 内のセグメント                                  |
| `t_start`  | `Real`   | 使用する `line` の開始時間 [s]                                        |
| `t_end`    | `Real`   | 使用する `line` の終了時間 [s]                                        |
| `map_name` | `Symbol` | (オプション) `line` に関連する磁気異常マップの名前、`y_type = :b, :c` の場合のみ使用されます |

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

  * `features_setup`:   含める特徴のベクトル
  * `features_no_norm`: (オプション) 正規化しない特徴のベクトル
  * `y_type`: (オプション) `y` ターゲットタイプ

      * `:a` = 異常場 #1、補償されたテールスティンガーの総場スカラー磁力計測定
      * `:b` = 異常場 #2、補間された `磁気異常マップ` の値
      * `:c` = 航空機場 #1、補償されていないキャビンの総場スカラー磁力計測定と補間された `磁気異常マップ` の値の差
      * `:d` = 航空機場 #2、補償されていないキャビンと補償されたテールスティンガーの総場スカラー磁力計測定の差
      * `:e` = BPF'd 総場、バンドパスフィルタされた補償されていないキャビンの総場スカラー磁力計測定
  * `use_mag`:      (オプション) `y` ターゲットベクトルに使用する補償されていないスカラー磁力計 {`:mag_1_uc` など}、`y_type = :c, :d, :e` の場合のみ使用
  * `use_mag_c`:    (オプション) `y` ターゲットベクトルに使用する補償されたスカラー磁力計 {`:mag_1_c` など}、`y_type = :a, :d` の場合のみ使用
  * `use_vec`:      (オプション) 外部トレス・ローソン `A` 行列に使用するベクトル磁力計 (フラックスゲート) {`:flux_a` など}
  * `terms`:        (オプション) `x` データ行列内の `A` に使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `terms_A`:      (オプション) 外部トレス・ローソン `A` 行列に使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:  (オプション) true の場合、スカラー磁力計測定から日周変動を引く
  * `sub_igrf`:     (オプション) true の場合、スカラー磁力計測定からIGRFを引く
  * `bpf_mag`:      (オプション) true の場合、`x` データ行列内のスカラー磁力計測定をバンドパスフィルタ
  * `reorient_vec`: (オプション) true の場合、ベクトル磁力計測定をボディフレームに合わせる
  * `l_window`:     (オプション) `N % l_window` でデータをトリム、`-1` は無視
  * `mod_TL`:       (オプション) true の場合、`use_mag` を使用して修正された外部トレス・ローソン `A` 行列を作成
  * `map_TL`:       (オプション) true の場合、マップベースの外部トレス・ローソン `A` 行列を作成
  * `return_B`:     (オプション) true の場合、`Bt` および `B_dot` も返す
  * `silent`:       (オプション) true の場合、出力を表示しない

**戻り値:**

  * `A`:        `N` x `N_TL` 外部トレス・ローソン `A` 行列 (`N_TL` はトレス・ローソン係数の数)
  * `x`:        `N` x `Nf` データ行列 (`Nf` は特徴の数)
  * `y`:        長さ `N` のターゲットベクトル
  * `no_norm`:  長さ `Nf` の正規化しない特徴のブールインデックス
  * `features`: 長さ `Nf` の特徴ベクトル (TL `A` の成分を含むなど)
  * `l_segs`:   長さ `N_lines` の `lines` の長さのベクトル、sum(l_segs) = `N`
  * `Bt`:       `return_B = true` の場合、`A` を作成するために使用された総場測定の長さ `N` の大きさ [nT]
  * `B_dot`:    `return_B = true` の場合、`A` を作成するために使用された総場ベクトルの有限差分 `N` x `3` [nT]
