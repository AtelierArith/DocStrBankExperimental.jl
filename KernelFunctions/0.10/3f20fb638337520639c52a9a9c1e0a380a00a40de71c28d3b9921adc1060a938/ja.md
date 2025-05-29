```
median_heuristic_transform(distance, x::AbstractVector)
```

入力を要素ごとに `x` のデータポイントの中央値 `distance` で割る [`ScaleTransform`](@ref) を作成します。

`distance` は `KernelFunctions.pairwise` でのペアワイズ評価をサポートする必要があります。パッケージ [Distances.jl](https://github.com/JuliaStats/Distances.jl) のすべての `PreMetric`（例えば `Euclidean`）は、この要件を自動的に満たします。

# 例

```jldoctest
julia> using Distances, Statistics

julia> x = ColVecs(rand(100, 10));

julia> t = median_heuristic_transform(Euclidean(), x);

julia> y = map(t, x);

julia> median(euclidean(y[i], y[j]) for i in 1:10, j in 1:10 if i != j) ≈ 1
true
```
