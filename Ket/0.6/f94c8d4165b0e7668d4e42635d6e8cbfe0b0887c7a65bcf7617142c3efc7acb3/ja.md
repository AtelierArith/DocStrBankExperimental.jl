```
permutation_matrix(dims::Union{Integer,AbstractVector}, perm::AbstractVector)
```

次元 `dims` のサブシステムを置換 `perm` に従って置換するユニタリ。`dims` が整数の場合、`length(perm)` のサブシステムが等しい次元 `dims` を持つと仮定します。
