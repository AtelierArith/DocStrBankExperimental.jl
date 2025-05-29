```
read_eig(filename)
read_eig(filename, ::FortranText)
read_eig(filename, ::FortranBinaryStream)
```

wannier90の`eig`ファイルを読み込みます。

# 戻り値

  * `eigenvalues`: 長さ`n_kpts`のベクトル、各要素は長さ`n_bands`のベクトルです

1つ目のバージョンは2つ目と3つ目のバージョンの便利なラッパー関数です。
