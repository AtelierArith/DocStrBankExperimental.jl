```
sparse_permute(sm::SparseMatrix, pr::Vector{Int}, pc::Vector{Int})
```

行と列のインデックスを置換することによってスパース行列を作成します。

ベクトル `pr` は行の置換を、`pc` は列の置換を示します。
