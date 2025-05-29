```
NGramExtractor{T} <: Extractor
```

Extracts `String` as `n-`grams (`Mill.NGramMatrix`).

# Examples

```jldoctest
julia> e = NGramExtractor()
NGramExtractor(n=3, b=256, m=2053)

julia> e("foo")
2053×1 ArrayNode{NGramMatrix{String, Vector{String}, Int64}, Nothing}:
 "foo"

```
