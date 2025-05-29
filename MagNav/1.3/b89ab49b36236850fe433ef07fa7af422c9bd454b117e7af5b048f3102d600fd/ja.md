```
comp_train(comp_params::CompParams, xyz_vec::Vector, ind_vec::Vector,
           mapS::Union{MapS,MapSd,MapS3D} = mapS_null;
           temp_params::TempParams        = TempParams(),
           xyz_test::XYZ                  = xyz_vec[1],
           ind_test                       = BitVector(),
           silent::Bool                   = false)
```

航空磁気補償モデルを訓練します。

**引数:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体、次のいずれか:

```
  * `NNCompParams`: ニューラルネットワークベースの航空磁気補償パラメータ構造体
  * `LinCompParams`: 線形航空磁気補償パラメータ構造体
```

  * `xyz_vec`:     `XYZ` フライトデータ構造体のベクトル
  * `ind_vec`:     選択されたデータインデックスのベクトル
  * `mapS`:        (オプション) `MapS`, `MapSd`, または `MapS3D` スカラー磁気異常マップ構造体、`y_type = :b, :c` のみで使用
  * `temp_params`: (オプション) `TempParams` 一時的な時間パラメータ構造体
  * `xyz_test`:    (オプション) 保持されたテストデータ構造体 `XYZ`
  * `ind_test`:    (オプション) テストデータ構造体のインデックス
  * `silent`:      (オプション) true の場合、出力なし

**戻り値:**

  * `comp_params`: `CompParams` 航空磁気補償パラメータ構造体
  * `y`:           長さ `N` のターゲットベクトル
  * `y_hat`:       長さ `N` の予測ベクトル
  * `err`:         長さ `N` の補償誤差
  * `features`:    長さ `Nf` の特徴ベクトル（TL `A` の成分などを含む）
