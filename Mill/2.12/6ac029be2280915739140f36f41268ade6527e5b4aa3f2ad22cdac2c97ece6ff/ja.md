```
NGramMatrix(s, n=3, b=256, m=2053)
```

[`NGramMatrix`](@ref)を構築します。`s`は単一のシーケンスまたは任意の`AbstractVector`であることができます。

# 例

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

関連情報: [`NGramIterator`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).
