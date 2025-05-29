```
CategoricalExtractor{V, I} <: Extractor
```

カテゴリ変数として解釈される単一のアイテムをワンホットエンコードされたベクトルに抽出します。

未知の値のために常に追加のカテゴリが存在します（したがって、表示される `n` はカテゴリの数よりも1つ多くなります）。

# 例

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
