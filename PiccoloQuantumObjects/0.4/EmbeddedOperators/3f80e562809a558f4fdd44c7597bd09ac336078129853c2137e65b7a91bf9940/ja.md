```
get_iso_vec_leakage_indices(subspace::AbstractVector{Int}, levels::Int)
get_iso_vec_leakage_indices(subspaces::AbstractVector{<:AbstractVector{Int}}, subsystem_levels::AbstractVector{Int})
get_iso_vec_leakage_indices(subsystem_levels::AbstractVector{Int}; subspace=1:2)
get_iso_vec_leakage_indices(op::EmbeddedOperator)
```

演算子の同型ベクトル空間における漏洩のインデックスを取得します。
