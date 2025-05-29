```
EmbeddedOperator(
    subspace_operator::AbstractMatrix{<:Number},
    subsystem_indices::AbstractVector{Int},
    subspaces::AbstractVector{<:AbstractVector{Int}},
    subsystem_levels::AbstractVector{Int}
)
```

与えられた `subspaces` に `subspace_operator` を埋め込みます。ここで、`subsystem_indices` は演算子が定義されているサブスペースをリストし、`subsystem_levels` は演算子が埋め込まれているサブシステムのレベルをリストします。
