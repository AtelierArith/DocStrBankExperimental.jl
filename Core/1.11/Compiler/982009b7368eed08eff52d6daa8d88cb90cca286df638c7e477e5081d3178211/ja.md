```
argextype(x, src::Union{IRCode,IncrementalCompact}) -> t
argextype(x, src::CodeInfo, sptypes::Vector{VarState}) -> t
```

値 `x` の型を推論されたソース `src` の文脈で返します。`t` は拡張された格子要素である可能性があることに注意してください。`widenconst(t)` を使用して `x` のネイティブな Julia 型を取得します。
