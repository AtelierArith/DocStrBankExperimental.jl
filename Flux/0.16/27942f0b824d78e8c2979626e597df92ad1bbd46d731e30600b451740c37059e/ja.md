```
truncated_normal([rng], size...; mean = 0, std = 1, lo = -2, hi = 2) -> Array
truncated_normal([rng]; kw...) -> Function
```

指定された `size` の `Array{Float32}` を返します。各要素は切断正規分布から抽出されます。数値は `filter(x -> lo<=x<=hi, mean .+ std .* randn(100))` のように分布します。

値は一様分布 (0, 1) (`rand()`) をサンプリングし、その後切断正規分布の逆CDFを適用することによって生成されます。この方法は `lo ≤ mean ≤ hi` の場合に最も効果的です。

# 例

```jldoctest
julia> using Statistics

julia> Flux.truncated_normal(3, 4) |> summary
"3×4 Matrix{Float32}"

julia> round.(extrema(Flux.truncated_normal(10^6)); digits=3)
(-2.0f0, 2.0f0)

julia> round(std(Flux.truncated_normal(10^6; lo = -100, hi = 100)))
1.0f0
```
