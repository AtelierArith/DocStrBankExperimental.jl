```
splitsign(BG::BisectionGrid)
```

バイセクショングリッドの評価されたポイントを正のポイントのベクトルと負のポイントのベクトルに分割します。

# 例

```jldoctest
julia> BG = bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=2)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.5:1.0, 0.0:0.5:1.0)
  Grid points: 9
  Evaluations: 9
        Edges: 4

julia> posx, negx = splitsign(BG);


julia> posx
4-element Vector{Tuple{Float64, Float64}}:
 (0.0, 0.0)
 (0.5, 0.0)
 (0.0, 0.5)
 (0.5, 0.5)

julia> negx
5-element Vector{Tuple{Float64, Float64}}:
 (1.0, 0.0)
 (1.0, 0.5)
 (0.0, 1.0)
 (0.5, 1.0)
 (1.0, 1.0)
```
