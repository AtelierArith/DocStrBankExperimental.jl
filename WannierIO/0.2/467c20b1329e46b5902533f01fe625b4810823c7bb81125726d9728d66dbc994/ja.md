```
write_chk(filename, chk::Chk; binary=false)
write_chk(filename, chk::Chk, ::FortranText)
write_chk(filename, chk::Chk, ::FortranBinary)
```

wannier90 `chk` ファイルを書きます。

[`write_amn`](@ref) と同様に、最初のバージョンは便利なラッパーです。

# キーワード引数

  * `binary`: Fortran バイナリファイルとして書き込むかどうか。wannier90 のデフォルトは Fortran バイナリ形式ですが、ここではデフォルトが `false` です。これは Fortran バイナリがコンパイラとプラットフォームに依存するため、常に動作することが保証されていないからです。
