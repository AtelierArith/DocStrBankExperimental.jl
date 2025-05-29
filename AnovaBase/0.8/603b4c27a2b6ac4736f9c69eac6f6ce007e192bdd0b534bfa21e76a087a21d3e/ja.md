```
MultiAovModels(model::NTuple{N, M}) where {M, N} -> NestedModels{M, N}
MultiAovModels(model::Vararg{M, N}) where {M, N} -> NestedModels{M, N}
MultiAovModels(model::T) where {T <: Tuple}      -> MixedAovModels
MultiAovModels(model...)                         -> MixedAovModels
```

モデルタイプに基づいて `NestedModels` または `MixedAovModels` を構築します。
