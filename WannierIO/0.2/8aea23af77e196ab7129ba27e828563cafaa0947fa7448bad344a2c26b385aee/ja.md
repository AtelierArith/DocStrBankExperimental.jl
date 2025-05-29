```julia
write_w90_band_kpt(filename; kpoints, kweights)

```

`prefix_band.kpt`ファイルを書き込みます。

# 引数

  * `filename`: `prefix_band.kpt`のファイル名

# キーワード引数

  * `kpoints`: 長さ`n_kpts`のベクトル、分数座標
  * `kweights`: `n_kpts`、オプション、k点の重み、デフォルトは1.0です。
