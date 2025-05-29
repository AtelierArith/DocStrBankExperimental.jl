```
read_spn(filename)
read_spn(filename, ::FortranText)
read_spn(filename, ::FortranBinary)
```

wannier90の`spn`ファイルを読み込みます。

# 戻り値

  * `Sx`: スピンx、長さ`n_kpts`のベクトル、各要素は`n_bands`-by-`n_bands`の行列
  * `Sy`: スピンy、長さ`n_kpts`のベクトル、各要素は`n_bands`-by-`n_bands`の行列
  * `Sz`: スピンz、長さ`n_kpts`のベクトル、各要素は`n_bands`-by-`n_bands`の行列
  * `header`: ファイルの1行目
