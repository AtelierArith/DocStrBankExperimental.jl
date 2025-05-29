```
SparseMatrixDict{Tv,Ti<:Integer} <: AbstractSparseMatrix{Tv,Ti}
s = SparseMatrixDict{Tv,Ti}(m,n)
```

辞書形式でスパース行列を格納するための行列タイプであり、Dict{Tuple{Ti,Ti},Tv}として表現されます。コンストラクタは2つの引数を受け取ります：行数 (m) と列数 (n)。
