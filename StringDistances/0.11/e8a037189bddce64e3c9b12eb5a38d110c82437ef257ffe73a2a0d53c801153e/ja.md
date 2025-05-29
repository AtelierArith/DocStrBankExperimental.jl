```
findnearest(s, itr, dist::Union{StringMetric, StringSemiMetric}) -> (x, index)
```

`findnearest`は、距離`dist`に従って`s`との距離が最も低い`itr`の要素の値とインデックスを返します。

これは特に[`Levenshtein`](@ref)および[`DamerauLevenshtein`](@ref)距離（および[`Partial`](@ref)、[`TokenSort`](@ref)、[`TokenSet`](@ref)、または[`TokenMax`](@ref)を介したその修正）に最適化されています。

### 例

```julia-repl
julia> using StringDistances
julia> s = "Newark"
julia> iter = ["New York", "Princeton", "San Francisco"]
julia> findnearest(s, iter, Levenshtein())
("NewYork", 1)
julia> findnearest(s, iter, Levenshtein(); min_score = 0.9)
(nothing, nothing)
```
