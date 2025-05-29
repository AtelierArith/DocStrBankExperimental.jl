```
Smith{T,M<:AbstractMatrix{T}} <: Factorization{T}
```

整数行列 `A` のスミス標準形 `S` への分解の結果を説明します。`S` は対角行列であり、`U` と `V` はユニモジュラー行列で、次の関係が成り立ちます：`S == U*A*V`、または同等に、`A == U\S/V`。
