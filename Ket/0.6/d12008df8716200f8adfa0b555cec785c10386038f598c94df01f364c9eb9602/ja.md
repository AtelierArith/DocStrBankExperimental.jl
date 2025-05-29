```
applymap_subsystem(op::AbstractMatrix, ψ::AbstractVector, subsystems::Integer, dims::AbstractVector = _equal_sizes(ρ))
```

演算子 `op` を `ρ` のサブシステムに適用し、`subsystems` によって特定されるサブシステムの結果を得ます。これは (op ⊗ I) * ψ になります。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
