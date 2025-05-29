```
NGramMatrix(s, n=3, b=256, m=2053)
```

Construct an [`NGramMatrix`](@ref). `s` can either be a single sequence or any `AbstractVector`.

# Examples

```jldoctest
julia> NGramMatrix([1,2,3])
2053×1 NGramMatrix{Vector{Int64}, Vector{Vector{Int64}}, Int64}:
 [1, 2, 3]

julia> NGramMatrix(["a", missing, "c"], 2, 128)
2053×3 NGramMatrix{Union{Missing, String}, Vector{Union{Missing, String}}, Union{Missing, Int64}}:
 "a"
 missing
 "c"
```

See also: [`NGramIterator`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).
