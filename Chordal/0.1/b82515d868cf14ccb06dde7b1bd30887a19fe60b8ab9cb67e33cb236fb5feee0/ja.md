```
sparsity_pattern(mats::AbstractVector{SparseMatrixCSC{T,S}}) where {T, S <: Integer}
```

`mats`内の行列の0/1集約スパースパターンをスパース行列として返します。
