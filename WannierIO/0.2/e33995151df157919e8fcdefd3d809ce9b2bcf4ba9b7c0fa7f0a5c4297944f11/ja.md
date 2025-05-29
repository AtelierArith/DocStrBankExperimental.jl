```julia
write_xsf(filename, lattice, atom_positions, atom_numbers)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin
)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin,
    span_vectors
)
write_xsf(
    filename,
    lattice,
    atom_positions,
    atom_numbers,
    origin,
    span_vectors,
    W
)

```

`xsf`ファイルを書き込みます。

# 引数

  * `lattice`: `3 * 3`, Å, 各列は格子ベクトル
  * `atom_positions`: 長さ`n_atoms`のベクトル、分数座標
  * `atom_numbers`: `n_atoms`, 原子番号
  * `origin`: `3`, Å, グリッドの原点
  * `span_vectors`: `3 * 3`, Å, 各列はスパンベクトル
  * `W`: `nx * ny * nz`, 体積データ
