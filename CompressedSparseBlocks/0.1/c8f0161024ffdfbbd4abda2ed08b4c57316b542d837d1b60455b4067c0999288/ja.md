```julia
mutable struct SparseMatrixCSB{Tv, Ti} <: SparseArrays.AbstractSparseArray{Tv, Ti, 2}
```

Compressed Sparse Blocks形式でスパース行列を格納するための行列タイプ。`SparseMatrixCSB`を構築する標準的な方法は、`SparseMatrixCSC`オブジェクトを渡すことです。コンストラクタを参照してください。
