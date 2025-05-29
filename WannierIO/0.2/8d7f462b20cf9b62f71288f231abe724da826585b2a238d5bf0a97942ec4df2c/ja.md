```
read_uIu(filename)
read_uIu(filename, ::FortranText; transpose_band_indices=true)
read_uIu(filename, ::FortranBinary; transpose_band_indices=true)
```

wannier90の`uIu`ファイルを読み込みます。

# キーワード引数

  * `transpose_band_indices`: QE pw2wannier90.xは行列を奇妙な転置された方法で書き込みます。QE生成の`uIu`ファイルを読み込む場合、このフラグは真であるべきで、バンドインデックスの順序を復元し、返される行列が正しい順序を持つようにします。すなわち、`uIu[ik][ib1, ib2][m, n]`は$\langle u_{m, k + b_1} | u_{n, k + b_2} \rangle$です。

# 戻り値

  * `uIu`: 長さ`n_kpts`のベクトルで、各要素は`n_bvecs * n_bvecs`の行列であり、各要素は`n_bands * n_bands`の行列です。
  * `header`: ファイルの1行目。
