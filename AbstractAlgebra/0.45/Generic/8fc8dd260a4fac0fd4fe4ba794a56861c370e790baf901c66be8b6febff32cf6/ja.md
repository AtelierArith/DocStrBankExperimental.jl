```
divrem(a::MPoly{T}, b::Vector{MPoly{T}}) where {T <: RingElement}
```

タプル `(q, r)` を返します。ここで、`q` は `b` の各多項式に対して1つの多項式からなる配列であり、`r` は `a = sum_i b[i]*q[i] + r` を満たす多項式です。
