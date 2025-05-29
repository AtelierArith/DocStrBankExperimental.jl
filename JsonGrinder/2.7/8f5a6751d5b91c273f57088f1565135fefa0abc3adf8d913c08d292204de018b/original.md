```
struct StableExtractor{T <: LeafExtractor} <: LeafExtractor
```

Wraps any other `LeafExtractor` and makes it output stable results w.r.t. missing input values.

See also: [`stabilizeextractor`](@ref).
