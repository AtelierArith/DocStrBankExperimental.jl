```
InfiniteMPOHamiltonian(Ws::Vector{<:Matrix})
```

ベクトルの行列から `InfiniteMPOHamiltonian` を作成します。ここで、`Ws[i][j, k]` はサイト `i`、左レベル `j` および右レベル `k` の演算子を表します。ここで、エントリは `MPOTensor`、`Missing` または `Number` のいずれかであることができます。
