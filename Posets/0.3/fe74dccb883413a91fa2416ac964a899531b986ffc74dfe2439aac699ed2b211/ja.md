```
weak_order(vals::Vector{T}) where {T<:Real}
```

実数のリストから弱順序 `p` を作成します。`p` の要素 `i` は、`vals[i] < vals[j]` が成り立つ場合に要素 `j` よりも小さいです。
