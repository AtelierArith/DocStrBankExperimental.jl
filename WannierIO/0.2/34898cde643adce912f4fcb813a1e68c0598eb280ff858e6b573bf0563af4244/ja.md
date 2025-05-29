```julia
read_w90_wsvec(filename)

```

`prefix_wsvec.dat`を読み込みます。

# 戻り値

  * `mdrs`: MDRS補間を使用するかどうか、すなわちヘッダーの`use_ws_distance`
  * `Rvectors`: $\mathbf{R}$-ベクトル
  * `Tvectors`: $\mathbf{T}_{m n \mathbf{R}}$-ベクトル。`mdrs = true`のときのみ返されます。
  * `Tdegens`: $\mathbf{T}_{m n \mathbf{R}}$-ベクトルの縮退度。`mdrs = true`のときのみ返されます。
  * `n_wann`: WFの数
  * `header`: ファイルの最初の行
