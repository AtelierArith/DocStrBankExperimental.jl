```
SimpleMetaArray(T::Type, dims::Dims{N}, metadata::DictOrNothing=nothing, colmetadata::Union{NTuple{N,DictOrNothing},DictOrNothing}=nothing) where N
SimpleMetaArray(A::Type{<:AbstractArray{T,N}}, dims::Dims{N}, metadata::DictOrNothing=nothing, colmetadata::Union{NTuple{N,DictOrNothing},DictOrNothing}=nothing) where {T,N}
```

与えられた型、次元、メタデータ、および列メタデータを使用して `SimpleMetaArray` を構築します。型は具体的な型または `AbstractArray` の具体的なサブタイプであることができます。
