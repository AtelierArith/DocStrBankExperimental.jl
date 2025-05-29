```
write_unk(filename, ik, Ψ; binary=false)
write_unk(filename, ik, Ψ, ::FortranText)
write_unk(filename, ik, Ψ, ::FortranBinary)
```

周期的な部分のBloch波動関数のための`UNK`ファイルを書きます。

# 引数

  * ik: どのk点で？ 1から始まります
  * Ψ: Bloch波動関数、`size(Ψ) = (n_gx, n_gy, n_gz, n_bands, n_spin)`

# キーワード引数

  * `binary`: Fortran非フォーマットファイルとして書き込みます
