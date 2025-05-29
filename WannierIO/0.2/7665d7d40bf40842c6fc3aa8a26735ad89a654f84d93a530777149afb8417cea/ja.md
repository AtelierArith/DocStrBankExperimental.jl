```
read_unk(filename)
read_unk(filename, ::FortranText)
read_unk(filename, ::FortranBinary)
```

wannier90 `UNK`ファイルを読み込み、Bloch波動関数の周期的部分を取得します。

# 戻り値

  * `ik`: k点インデックス、1から始まる
  * `Ψ`: 実空間におけるBloch波動関数の周期的部分、サイズ = `(n_gx, n_gy, n_gz, n_bands, n_spin)`
