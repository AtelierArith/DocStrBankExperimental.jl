```
applymap_subsystem(op::AbstractMatrix, ψ::AbstractVector, subsystems::AbstractVector, dims::AbstractVector = _equal_sizes(ρ))
```

演算子 `op` を `subsystems` によって特定された `ρ` のサブシステムに適用し、(op ⊗ I) * ψ を得ます。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
