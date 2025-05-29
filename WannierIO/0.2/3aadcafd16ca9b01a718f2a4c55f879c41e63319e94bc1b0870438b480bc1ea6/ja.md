```
write_amn(filename, A; header=default_header(), binary=false)
write_amn(filename, A, ::FortranText; header=default_header())
write_amn(filename, A, ::FortranBinaryStream; header=default_header())
```

wannier90 `amn` ファイルを書きます。

# 引数

  * `filename`: 出力ファイル名
  * `A`: 長さ `n_kpts` のベクトル、各要素は `n_bands * n_wann` 行列です

# キーワード引数

  * `header`: ファイルの1行目
  * `binary`: Fortranの非フォーマットファイルとして書き込みます。これはWannier90のデフォルトです。ここで `binary` kwargs は便利のために提供されています。

[`read_amn`](@ref) と同様に、この関数には3つのバージョンがあります。最初のものはラッパー関数で、`binary` kwargs に応じて2番目または3番目のバージョンを呼び出します。
