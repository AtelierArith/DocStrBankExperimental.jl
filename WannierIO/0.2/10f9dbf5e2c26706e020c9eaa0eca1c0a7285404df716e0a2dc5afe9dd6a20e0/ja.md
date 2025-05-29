```julia
write_w90_band_dat(filename; x, eigenvalues, extras)

```

`prefix_band.dat`ファイルを書き込みます。

# 引数

  * `filename`: `prefix_band.dat`のファイル名

# キーワード引数

  * `x`: `n_kpts`、x軸の値、直交長さで
  * `eigenvalues`: 長さ`n_kpts`のベクトル、各要素は長さ`n_bands`のバンドエネルギーのベクトル
  * `extras`: オプション、`eigenvalues`と同じサイズ、`prefix_band.dat`の3列目として書き込まれます。`postw90.x`によって生成された`prefix-band.dat`ファイルには、時々、例えば固有値の色のための3列目があります。
