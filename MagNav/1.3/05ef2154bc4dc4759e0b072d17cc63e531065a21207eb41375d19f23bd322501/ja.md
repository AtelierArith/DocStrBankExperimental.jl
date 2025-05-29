```
get_x(xyz::XYZ, ind = trues(xyz.traj.N),
      features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
      features_no_norm::Vector{Symbol} = Symbol[],
      terms             = [:permanent,:induced,:eddy],
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false,
      bpf_mag::Bool     = false)
```

`x` データ行列を取得します。

**引数:**

  * `xyz`:              `XYZ` フライトデータ構造体
  * `ind`:              選択されたデータインデックス
  * `features_setup`:   含める特徴のベクトル
  * `features_no_norm`: (オプション) 正規化しない特徴のベクトル
  * `terms`:            (オプション) 使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:      (オプション) true の場合、スカラー磁力計測定から日周変動を引く
  * `sub_igrf`:         (オプション) true の場合、スカラー磁力計測定からIGRFを引く
  * `bpf_mag`:          (オプション) true の場合、スカラー磁力計測定を bpf する

**戻り値:**

  * `x`:        `N` x `Nf` データ行列 (`Nf` は特徴の数)
  * `no_norm`:  長さ-`Nf` の正規化しない特徴のブールインデックス
  * `features`: 長さ-`Nf` の特徴ベクトル (TL `A` の成分などを含む)
  * `l_segs`:   長さ-`N_lines` の `lines` の長さのベクトル、sum(l_segs) = `N`
