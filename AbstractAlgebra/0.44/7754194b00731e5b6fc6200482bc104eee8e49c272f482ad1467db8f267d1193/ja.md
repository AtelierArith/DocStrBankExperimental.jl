```
map(f, a::MatrixElem{T}) where T <: NCRingElement
```

行列 `a` の各要素に `f` を適用することで行列を変換します。これは `map_entries(f, a)` と同等です。
