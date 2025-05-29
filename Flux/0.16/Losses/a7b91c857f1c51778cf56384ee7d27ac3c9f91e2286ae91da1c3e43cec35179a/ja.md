```
kldivergence(ŷ, y; agg = mean, eps = eps(eltype(ŷ)))
```

与えられた確率分布の間の[Kullback-Leiblerダイバージェンス](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)を返します。

KLダイバージェンスは、1つの確率分布が他の分布とどれだけ異なるかを測る指標です。常に非負であり、両方の分布が等しいときのみゼロになります。

# 例

```jldoctest
julia> p1 = [1 0; 0 1]
2×2 Matrix{Int64}:
 1  0
 0  1

julia> p2 = fill(0.5, 2, 2)
2×2 Matrix{Float64}:
 0.5  0.5
 0.5  0.5

julia> Flux.kldivergence(p2, p1) ≈ log(2)
true

julia> Flux.kldivergence(p2, p1; agg = sum) ≈ 2log(2)
true

julia> Flux.kldivergence(p2, p2; eps = 0)  # 約 -2e-16 レギュレーター付き
0.0

julia> Flux.kldivergence(p1, p2; eps = 0)  # 約 17.3 レギュレーター付き
Inf
```
