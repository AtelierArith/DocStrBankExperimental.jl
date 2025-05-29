```
map(f, a::MatrixElem{T}) where T <: NCRingElement
```

行列 `a` を変換し、各要素に `f` を適用します。これは `map_entries(f, a)` と同等です。
