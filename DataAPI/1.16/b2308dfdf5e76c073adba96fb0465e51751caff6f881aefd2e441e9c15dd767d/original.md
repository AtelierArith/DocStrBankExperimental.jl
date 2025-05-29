```
colmetadatasupport(T::Type)
```

Return a `NamedTuple{(:read, :write), Tuple{Bool, Bool}}` indicating whether values of type `T` support column metadata.

The `read` field indicates whether reading metadata with the [`colmetadata`](@ref) and [`colmetadatakeys`](@ref) functions is supported.

The `write` field indicates whether modifying metadata with the [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), and [`emptycolmetadata!`](@ref) functions is supported.
