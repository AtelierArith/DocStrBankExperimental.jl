```
applymap_subsystem(K::AbstractVector{<:AbstractMatrix}, ρ::AbstractMatrix, subsystems::Integer, dims::AbstractVector = _equal_sizes(ρ))
```

`K`のクローズ演算子を`ρ`の`subsystems`で特定されたサブシステムに適用し、∑ᵢ(K[i] ⊗ I) * ρ * (K[i]' ⊗ I)を得ます。引数`dims`が省略された場合、2つの同じサイズのサブシステムが仮定されます。
