```
write_eig(filename, eigenvalues; binary=false)
write_eig(filename, eigenvalues, ::FortranText)
write_eig(filename, eigenvalues, ::FortranBinaryStream)
```

`eig`ファイルを書きます。

# 引数

  * `eigenvalues`: 長さ`n_kpts`のベクトル、各要素は長さ`n_bands`のベクトルです。

# キーワード引数

  * `binary`: trueの場合、Fortranバイナリ形式で書き込みます。
