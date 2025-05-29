```
NGramExtractor{T} <: Extractor
```

`String`を`n-`グラム（`Mill.NGramMatrix`）として抽出します。

# 例

```jldoctest
julia> e = NGramExtractor()
NGramExtractor(n=3, b=256, m=2053)

julia> e("foo")
2053×1 ArrayNode{NGramMatrix{String, Vector{String}, Int64}, Nothing}:
 "foo"

```
