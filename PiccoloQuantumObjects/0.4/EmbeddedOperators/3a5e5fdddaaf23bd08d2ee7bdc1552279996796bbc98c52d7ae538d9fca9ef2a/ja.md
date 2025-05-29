```
get_subspace_indices(subspace::AbstractVector{Int}, levels::Int)
get_subspace_indices(subspaces::Vector{<:AbstractVector{Int}}, subsystem_levels::AbstractVector{Int})
get_subspace_indices(subsystem_levels::AbstractVector{Int}; subspace=1:2)
get_subspace_indices(op::EmbeddedOperator)
```

量子システムの提供されたサブスペースのインデックスを取得します。
