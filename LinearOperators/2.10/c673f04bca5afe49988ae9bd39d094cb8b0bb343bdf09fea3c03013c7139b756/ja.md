```
LinearOperator(M::AbstractMatrix{T}; symmetric=false, hermitian=false, S = Vector{T}) where {T}
```

密行列または疎行列から線形演算子を構築します。オプションのキーワード引数を使用して、演算子が対称であるかどうか、またはエルミートであるかどうかを示します。`S`を使用してGPU上のLinearOperatorsに変更します。
