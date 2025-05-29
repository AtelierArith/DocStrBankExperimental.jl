```
entanglement_entropy(ψ::AbstractVector, dims::AbstractVecOrTuple = _equal_sizes(ψ))
```

二部純状態 `ψ` のエンタングルメントエントロピーを、部分系の次元 `dims` を用いて計算します。引数 `dims` が省略された場合、同じサイズの部分系が仮定されます。
