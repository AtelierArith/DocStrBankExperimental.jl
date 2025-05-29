```
common_eigenspaces(L::Vector{<: MatElem{T}}; side::Symbol = :left)
  where T <: FieldElem -> Dict{Vector{T}, MatElem{T}}
```

行列 `L` の固有値のベクトルをキーとし、対応する固有空間を値とする辞書を返します。すなわち、`(k, v)` がキーと値のペアである場合、`v` はすべての `i` に対して固有値 `k[i]` に関する `L[i]` の固有空間です。`side` が `:right` の場合は右固有空間が計算され、`:left` の場合は左固有空間が計算されます。
