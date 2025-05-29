```julia
write_w90_band_labelinfo(
    filename;
    x,
    kpoints,
    symm_point_indices,
    symm_point_labels
)

```

`prefix_band.labelinfo`ファイルを書きます。

# 引数

  * `filename`: `prefix_band.labelinfo`のファイル名

# キーワード引数

  * `x`: `n_kpts`-ベクトル、x軸の値、直交長さで
  * `kpoints`: 長さ`n_kpts`のベクトル、分数座標
  * `symm_point_indices`: `prefix_band.dat`における高対称点のインデックス
  * `symm_point_labels`: 高対称点の名前
