```julia
read_w90_band_dat(filename)

```

`wannier90.x`によって生成された`prefix_band.dat`ファイル、または`postw90.x`によって生成された`prefix-band.dat`ファイルを読み込みます。

# 戻り値

  * `x`: `n_kpts`、kpathのx軸値、直交長さ
  * `eigenvalues`: 長さ`n_kpts`のベクトル、各要素は長さ`n_bands`のバンドエネルギーのベクトル
  * `extras`: オプション（`postw90.x`は3列目のあるファイルを生成する場合があります）、`eigenvalues`と同じサイズで、各固有値の色、例えばスピン投影などが含まれます。
