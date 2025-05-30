```julia
mutable struct ExtendableSparseMatrix{Tv, Ti<:Integer} <: SparseArrays.AbstractSparseArray{Tv, Ti<:Integer, 2}
```

拡張可能なスパース行列。この行列の非ゼロエントリは、cscmatrixまたはlnkmatrixのいずれかに含まれ、両方には含まれません。

  * `cscmatrix::SparseArrays.SparseMatrixCSC`: 最終的な行列データ
  * `lnkmatrix::Union{Nothing, ExtendableSparse.SparseMatrixLNK{Tv, Ti}} where {Tv, Ti<:Integer}`: 拡張のデータを保持するリンクリスト構造
  * `phash::UInt64`: パターンハッシュ
