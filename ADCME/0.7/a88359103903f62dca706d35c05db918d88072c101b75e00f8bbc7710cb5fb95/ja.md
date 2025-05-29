```
mpi_SparseTensor(rows::Union{Array{Int32,1}, PyObject}, ncols::Union{Array{Int32,1}, PyObject}, cols::Union{Array{Int32,1}, PyObject},
    vals::Union{Array{Float64,1}, PyObject}, ilower::Int64, iupper::Int64, N::Int64)
```

現在のMPIプロセッサ用に$N\times N$の分散スパーステンソル`A`を作成します。現在のMPIプロセッサは、インデックス`[ilower, iupper]`を持つ行を所有します。サブマトリックスはCSR形式を使用して指定されます。

  * `rows`: 非ゼロ値を含む行を示す配列。`rows ≥ ilower`に注意してください。
  * `ncols`: `rows`内の各行の非ゼロ値の数を示す配列。
  * `cols`: 非ゼロ値の列インデックス。長さは$\sum_{i=1}^{\mathrm{ncols}} \mathrm{ncols}_i$です。
  * `vals`: `cols`内の各列インデックスに対応する非ゼロ値。

デフォルトでは、インデックスはゼロベースです。
