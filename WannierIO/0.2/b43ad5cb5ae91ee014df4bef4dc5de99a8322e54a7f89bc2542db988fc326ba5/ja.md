```julia
write_cube(
    filename,
    atom_positions,
    atom_numbers,
    origin,
    voxel_vectors,
    W
)

```

`cube`ファイルを書き込みます。

# 引数

  * `atom_positions`: `3 * n_atoms`、Å、直交座標
  * `atom_numbers`: `n_atoms`、原子番号
  * `origin`: `3`、Å、グリッドの原点
  * `voxel_vectors`: `3 * 3`、Å、各列はボクセルベクトル
  * `W`: `nx * ny * nz`、体積データ
