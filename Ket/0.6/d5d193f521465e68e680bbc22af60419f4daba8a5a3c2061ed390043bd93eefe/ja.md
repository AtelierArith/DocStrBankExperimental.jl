```
applymap_subsystem(K::AbstractVector{<:AbstractSparseArray}, ρ::AbstractSparseArray, subsystems::AbstractVector{<:Integer}, dims::AbstractVector = _equal_sizes(ρ))
```

スパース行列 `ρ` のサブシステムに `K` のスパースクラウス演算子を適用します。これは、∑ᵢ(K[i] ⊗ I) * ρ * (K[i]' ⊗ I) の結果になります。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
