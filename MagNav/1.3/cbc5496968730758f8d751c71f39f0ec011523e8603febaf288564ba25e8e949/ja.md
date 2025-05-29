```
comp_train(comp_params::CompParams, xyz::XYZ, ind,
           mapS::Union{MapS,MapSd,MapS3D} = mapS_null;
           temp_params::TempParams        = TempParams(),
           xyz_test::XYZ                  = xyz,
           ind_test                       = BitVector(),
           silent::Bool                   = false)
```

航空磁気補償モデルをトレーニングします。

**引数:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体、次のいずれか:

```
  * `NNCompParams`: ニューラルネットワークベースの航空磁気補償パラメータ構造体
  * `LinCompParams`: 線形航空磁気補償パラメータ構造体
```

  * `xyz`:         `XYZ` フライトデータ構造体
  * `ind`:         選択されたデータインデックス
  * `mapS`:        (オプション) `MapS`, `MapSd`, または `MapS3D` スカラー磁気異常マップ構造体、`y_type = :b, :c` のみで使用
  * `temp_params`: (オプション) `TempParams` 一時的な時間パラメータ構造体
  * `xyz_test`:    (オプション) `XYZ` ホールドアウトテストデータ構造体
  * `ind_test`:    (オプション) テストデータ構造体のインデックス
  * `silent`:      (オプション) true の場合、出力なし

**戻り値:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体
  * `y`:           長さ-`N` ターゲットベクトル
  * `y_hat`:       長さ-`N` 予測ベクトル
  * `err`:         長さ-`N` 補償誤差
  * `features`:    長さ-`Nf` 特徴ベクトル（TL `A` の成分などを含む）
