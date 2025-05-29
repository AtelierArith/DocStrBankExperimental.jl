```
divrem(a::MPoly{T}, b::Vector{MPoly{T}}) where {T <: RingElement}
```

多項式の配列 `q` と多項式 `r` からなるタプル `(q, r)` を返します。ここで `q` は `b` の各多項式に対するもので、`r` は `a = sum_i b[i]*q[i] + r` を満たす多項式です。
