```
ScalarExtractor{T} <: Extractor
```

数値を抽出し、`c`を引いて中心を取り、`s`でスケーリングします。

# 例

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
