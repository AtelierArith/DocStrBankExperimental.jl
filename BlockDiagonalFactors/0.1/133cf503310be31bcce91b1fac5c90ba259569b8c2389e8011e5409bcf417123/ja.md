```julia
factorize(As::Vector{SparseMatrixCSC{ComplexF64,Int}}, I::Vector{Int})

ブロック対角（遅延）因子の配列を作成します。行列の配列 `As` の各行列に対して `factorize` を呼び出し、インデックス `I` と共にそれらを保存します。
```
