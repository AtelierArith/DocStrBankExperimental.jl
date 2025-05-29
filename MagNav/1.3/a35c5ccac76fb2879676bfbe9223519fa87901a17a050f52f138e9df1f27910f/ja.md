```
comp_test(comp_params::CompParams, xyz::XYZ, ind,
          mapS::Union{MapS,MapSd,MapS3D} = mapS_null;
          temp_params::TempParams        = TempParams(),
          silent::Bool                   = false)
```

エアロマグネティック補償モデルの性能を評価します。

**引数:**

  * `comp_params`: `CompParams` エアロマグネティック補償パラメータ構造体、いずれか:

      * `NNCompParams`: ニューラルネットワークベースのエアロマグネティック補償パラメータ構造体
      * `LinCompParams`: 線形エアロマグネティック補償パラメータ構造体
  * `xyz`:         `XYZ` フライトデータ構造体
  * `ind`:         選択されたデータインデックス
  * `mapS`:        (オプション) `MapS`, `MapSd`, または `MapS3D` スカラー磁気異常マップ構造体、`y_type = :b, :c` のみで使用
  * `temp_params`: (オプション) `TempParams` 一時的な時間パラメータ構造体
  * `silent`:      (オプション) true の場合、出力なし

**戻り値:**

  * `y`:        長さ-`N` のターゲットベクトル
  * `y_hat`:    長さ-`N` の予測ベクトル
  * `err`:      長さ-`N` の補償誤差
  * `features`: 長さ-`Nf` の特徴ベクトル（TL `A` の成分などを含む）
