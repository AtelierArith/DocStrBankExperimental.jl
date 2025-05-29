```julia
find_subnetworks(M, bus_numbers)

```

考慮されるシステムに存在するサブネットワークを見つけます。これは、ABAまたは隣接行列を取ることによって評価されます。

# 引数

  * `M::SparseArrays.SparseMatrixCSC`:       入力スパース行列。
  * `bus_numbers::Vector{Int}`:       システムのバスのインデックスを含むベクター。
