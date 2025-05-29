```
entanglement_entropy(ρ::AbstractMatrix, dims::AbstractVecOrTuple = _equal_sizes(ρ), n::Integer = 1; verbose = false)
```

二部状態 `ρ` のエンタングルメントの相対エントロピーの下限を、サブシステムの次元 `dims` を使用して、DPS階層のレベル `n` で計算します。引数 `dims` が省略された場合、同じサイズのサブシステムが仮定されます。
