```julia
semilinear_form(
    exprs::AbstractArray,
    vars
) -> Tuple{SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, Any}

```

スパース行列 `A` と残差ベクトル `c` のタプルを返します。ここで、`A * vars + c` は `exprs` と同じです。
