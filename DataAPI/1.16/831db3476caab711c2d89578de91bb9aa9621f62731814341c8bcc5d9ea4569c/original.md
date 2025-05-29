```
metadatasupport(T::Type)
```

Return a `NamedTuple{(:read, :write), Tuple{Bool, Bool}}` indicating whether values of type `T` support metadata.

The `read` field indicates whether reading metadata with the [`metadata`](@ref) and [`metadatakeys`]](@ref) functions is supported.

The `write` field indicates whether modifying metadata with the [`metadata!`](@ref), [`deletemetadata!`](@ref), and [`emptymetadata!`](@ref) functions is supported.
