```
get_x(xyz_vec::Vector{XYZ}, ind_vec,
      features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
      features_no_norm::Vector{Symbol} = Symbol[],
      terms             = [:permanent,:induced,:eddy],
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false,
      bpf_mag::Bool     = false)
```

複数の `XYZ` フライトデータ構造体から `x` データ行列を取得します。

**引数:**

  * `xyz_vec`:          `XYZ` フライトデータ構造体のベクトル
  * `ind_vec`:          選択されたデータインデックスのベクトル
  * `features_setup`:   含める特徴のベクトル
  * `features_no_norm`: (オプション) 正規化しない特徴のベクトル
  * `terms`:            (オプション) 使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:      (オプション) true の場合、スカラー磁力計測定から日周変動を引く
  * `sub_igrf`:         (オプション) true の場合、スカラー磁力計測定から IGRF を引く
  * `bpf_mag`:          (オプション) true の場合、スカラー磁力計測定を bpf する

**戻り値:**

  * `x`:        `N` x `Nf` データ行列 (`Nf` は特徴の数)
  * `no_norm`:  正規化されない特徴の長さ-`Nf` ブールインデックス
  * `features`: 長さ-`Nf` 特徴ベクトル (TL `A` の成分などを含む)
  * `l_segs`:   長さ-`N_lines` のベクトルで、`lines` の長さ、sum(l_segs) = `N`
