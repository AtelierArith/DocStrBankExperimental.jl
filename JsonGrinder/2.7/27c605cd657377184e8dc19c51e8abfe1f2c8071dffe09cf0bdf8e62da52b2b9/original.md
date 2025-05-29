```
CategoricalExtractor{V, I} <: Extractor
```

Extracts a single item interpreted as a categorical variable into a one-hot encoded vector.

There is always an extra category for an unknown value (and hence the displayed `n` is one more than the number of categories).

# Examples

```jldoctest
julia> e = CategoricalExtractor(1:3)
CategoricalExtractor(n=4)

julia> e(2)
4×1 ArrayNode{OneHotMatrix{UInt32, Vector{UInt32}}, Nothing}:
 ⋅
 1
 ⋅
 ⋅

julia> e(-1)
4×1 ArrayNode{OneHotMatrix{UInt32, Vector{UInt32}}, Nothing}:
 ⋅
 ⋅
 ⋅
 1
```
