```
cosine_similarity(u::AbstractVector, v::AbstractVector) -> Float
```

Compute the cosine similarity of two vectors.

# Examples

```jldoctest
julia> cosine_similarity([1, 0], [1, 0])
1.0

julia> round(cosine_similarity([1,1], [1,0]), digits=3)
0.707

julia> cosine_similarity([1, 0], [0, 1])
0.0

julia> cosine_similarity([-1, 0], [1, 0])
-1.0

julia> round(cosine_similarity([1,0,0], [1,1,1]), digits=3)
0.577
```
