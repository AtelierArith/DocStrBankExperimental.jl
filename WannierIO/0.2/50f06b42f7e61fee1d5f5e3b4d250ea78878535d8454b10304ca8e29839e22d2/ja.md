```julia
write_w90_band(
    prefix;
    x,
    eigenvalues,
    kpoints,
    kweights,
    symm_point_indices,
    symm_point_labels
)

```

`prefix_band.dat, prefix_band.kpt, prefix_band.labelinfo.dat`を書き込みます。

# 引数

  * `prefix`: `prefix_band.dat, prefix_band.kpt, prefix_band.labelinfo.dat`の接頭辞

# キーワード引数

  * `x`: `n_kpts`、x軸の値、直交長さで
  * `eigenvalues`: 長さ`n_kpts`のベクトル、各要素は長さ`n_bands`のバンドエネルギーのベクトル
  * `kpoints`: 長さ`n_kpts`のベクトル、分数座標
  * `kweights`: 長さ`n_kpts`のベクトル、k点の重み
  * `symm_point_indices`: `prefix_band.dat`における高対称点のインデックス
  * `symm_point_labels`: 高対称点の名前
