```
style = StreamIndexStyle(A)
```

A trait that indicates the degree of support for indexing the streaming axes of `A`. Choices are [`IndexAny()`](@ref) and [`IndexIncremental()`](@ref) (for arrays that only permit advancing the time axis, e.g., a video stream from a webcam). The default value is `IndexAny()`.

This should be specialized for the type rather than the instance. For a StreamingContainer `S`, you can define this trait via

```julia
StreamIndexStyle(::Type{P}, ::typeof(f!)) = IndexIncremental()
```

where `P = typeof(parent(S))`.
