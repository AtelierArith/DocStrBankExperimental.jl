```
read_chk(filename)
read_chk(filename, ::FortranText)
read_chk(filename, ::FortranBinary)
```

wannier90 `chk` チェックポイントファイルを読み込みます。

[`read_amn`](@ref) と同様に、1 番目のバージョンは `chk` ファイル形式（バイナリまたはテキスト）を自動的に検出して読み込みます。
