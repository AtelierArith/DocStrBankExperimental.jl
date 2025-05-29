```
rref(M::SMat{T}; truncate = false) where {T <: FieldElement} -> (Int, SMat{T})
```

行列 $M$ の階数 $r$ と $M$ の簡約行基本形 $A$ からなるタプル $(r, A)$ を返します。`truncate = true` で関数が呼び出された場合、結果にはゼロ行が含まれないため、`nrows(A) == rank(M)` となります。
