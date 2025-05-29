```julia
read_w90_tbdat(filename)

```

`prefix_tb.dat`を読み込みます。

# 戻り値

  * `lattice`: 各列はÅ単位の格子ベクトル
  * `Rvectors`: 演算子が定義されている$\mathbf{R}$-ベクトル
  * `Rdegens`: 各$\mathbf{R}$-ベクトルの縮退度
  * `H`: ハミルトニアン$\mathbf{H}(\mathbf{R})$
  * `r_x`: 位置演算子の$x$成分
  * `r_y`: 位置演算子の$y$成分
  * `r_z`: 位置演算子の$z$成分
  * `header`: ファイルの最初の行
