```
read_mmn(filename)
read_mmn(filename, ::FortranText)
read_mmn(filename, ::FortranBinaryStream)
```

wannier90 `mmn` ファイルを読み込みます。

# 戻り値

  * `M`: 長さ-`n_kpts` のベクトルで、各要素は長さ-`n_bvecs` のベクトルであり、さらに各要素は `n_bands * n_bands` の行列です。
  * `kpb_k`: 長さ-`n_kpts` のベクトルで、各要素は隣接する k点のインデックスの整数の長さ-`n_bvecs` のベクトルです。
  * `kpb_G`: 長さ-`n_kpts` のベクトルで、各要素は `Vec3{Int}` の長さ-`n_bvecs` のベクトルであり、これは変換ベクトルです。
  * `header`: ファイルの1行目

変換ベクトル `G` は `b = kpoints[kpb_k[ik][ib]] + kpb_G[ik][ib] - kpoints[ik]` と定義され、ここで `b` は `ik` 番目の k点の `ib` 番目の bベクトルです。

最初のバージョンは他の2つの便利なラッパーです。
