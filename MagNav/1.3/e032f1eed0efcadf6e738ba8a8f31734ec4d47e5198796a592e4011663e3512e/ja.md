```
comp_train_test(comp_params::CompParams,
                xyz_train::XYZ, xyz_test::XYZ, ind_train, ind_test,
                mapS_train::Union{MapS,MapSd,MapS3D} = mapS_null,
                mapS_test::Union{MapS,MapSd,MapS3D}  = mapS_null;
                temp_params::TempParams = TempParams(),
                silent::Bool            = false)
```

航空磁気補償モデルのトレーニングと性能評価を行います。

**引数:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体、次のいずれか:

      * `NNCompParams`: ニューラルネットワークベースの航空磁気補償パラメータ構造体
      * `LinCompParams`: 線形航空磁気補償パラメータ構造体
  * `xyz_train`:   `XYZ` トレーニング用の飛行データ構造体
  * `xyz_test`:    `XYZ` テスト用の飛行データ構造体
  * `ind_train`:   トレーニング用に選択されたデータインデックス
  * `ind_test`:    テスト用に選択されたデータインデックス
  * `mapS_train`:  （オプション）トレーニング用の `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体、`y_type = :b, :c` のみで使用
  * `mapS_test`:   （オプション）テスト用の `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体、`y_type = :b, :c` のみで使用
  * `temp_params`: （オプション）`TempParams` 一時的な時間パラメータ構造体
  * `silent`:      （オプション）trueの場合、出力なし

**戻り値:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体
  * `y_train`:     長さ`N_train`のトレーニングターゲットベクトル
  * `y_train_hat`: 長さ`N_train`のトレーニング予測ベクトル
  * `err_train`:   長さ`N_train`のトレーニング補償誤差
  * `y_test`:      長さ`N_test`のテストターゲットベクトル
  * `y_test_hat`:  長さ`N_test`のテスト予測ベクトル
  * `err_test`:    長さ`N_test`のテスト補償誤差
  * `features`:    長さ`Nf`の特徴ベクトル（TL `A` の成分などを含む）
