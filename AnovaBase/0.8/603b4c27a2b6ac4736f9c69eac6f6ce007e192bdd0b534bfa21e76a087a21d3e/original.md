```
MultiAovModels(model::NTuple{N, M}) where {M, N} -> NestedModels{M, N}
MultiAovModels(model::Vararg{M, N}) where {M, N} -> NestedModels{M, N}
MultiAovModels(model::T) where {T <: Tuple}      -> MixedAovModels
MultiAovModels(model...)                         -> MixedAovModels
```

Construct `NestedModels` or `MixedAovModels` based on model types.
