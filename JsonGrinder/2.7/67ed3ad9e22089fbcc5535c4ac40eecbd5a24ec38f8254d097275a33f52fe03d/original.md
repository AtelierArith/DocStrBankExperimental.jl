```
ScalarExtractor{T} <: Extractor
```

Extracts a numerical value, centered by subtracting `c` and scaled by `s`.

# Examples

```jldoctest
julia> e = ScalarExtractor(2, 3)
ScalarExtractor(c=2.0, s=3.0)

julia> e(0)
1×1 ArrayNode{Matrix{Float32}, Nothing}:
 -6.0

julia> e(1)
1×1 ArrayNode{Matrix{Float32}, Nothing}:
 -3.0
```
