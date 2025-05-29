```
comp_train_test(comp_params::CompParams, lines_train, lines_test,
                df_line::DataFrame, df_flight::DataFrame, df_map::DataFrame;
                temp_params::TempParams = TempParams(),
                silent::Bool            = false)
```

航空磁気補償モデルのトレーニングと性能評価を行います。

**引数:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体、いずれか:

      * `NNCompParams`: ニューラルネットワークベースの航空磁気補償パラメータ構造体
      * `LinCompParams`: 線形航空磁気補償パラメータ構造体
  * `lines_train`: トレーニング用に選択されたライン番号
  * `lines_test`: テスト用に選択されたライン番号
  * `df_line`:     `lines` のルックアップテーブル (DataFrame)

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
| `xyz_set`  | `Real`   | フライトデータセット番号 (異なる磁力計の位置などの不適切なデータセットの混合を防ぐために使用)                     |
| `xyz_file` | `String` | フライトデータのCSV、HDF5、またはMATファイルのパス/名前 (`.csv`, `.h5`, または `.mat` 拡張子が必要) |

  * `df_map`: マップデータファイルのルックアップテーブル (DataFrame)

| **フィールド**  | **型**    | **説明**                                                |
|:---------- |:-------- |:----------------------------------------------------- |
| `map_name` | `Symbol` | 磁気異常マップの名前                                            |
| `map_file` | `String` | マップデータのHDF5またはMATファイルのパス/名前 (`.h5` または `.mat` 拡張子が必要) |

  * `temp_params`: (オプション) `TempParams` 一時的な時間パラメータ構造体
  * `silent`:      (オプション) trueの場合、出力は行われません

**戻り値:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体
  * `y_train`:     長さ-`N_train` のトレーニングターゲットベクトル
  * `y_train_hat`: 長さ-`N_train` のトレーニング予測ベクトル
  * `err_train`:   長さ-`N_train` の平均補正済み (ラインごと) トレーニング補償誤差
  * `y_test`:      長さ-`N_test` のテストターゲットベクトル
  * `y_test_hat`:  長さ-`N_test` のテスト予測ベクトル
  * `err_test`:    長さ-`N_test` の平均補正済み (ラインごと) テスト補償誤差
  * `features`:    長さ-`Nf` の特徴ベクトル (TL `A` の成分などを含む)
