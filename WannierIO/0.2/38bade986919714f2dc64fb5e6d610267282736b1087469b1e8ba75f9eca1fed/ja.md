```julia
read_w90_hrdat(filename)

```

`prefix_hr.dat`を読み込みます。

# 戻り値

  * `Rvectors`: 演算子が定義されている$\mathbf{R}$-ベクトル
  * `Rdegens`: 各$\mathbf{R}$-ベクトルの縮退度
  * `H`: ハミルトニアン$\mathbf{H}(\mathbf{R})$
  * `header`: ファイルの最初の行
