```
unpack(Q::BayesianGenerator)
```

ベイジアンジェネレーターオブジェクトをそのパラメータに展開します。

# 引数

  * `Q::BayesianGenerator`: 展開するベイジアンジェネレーターオブジェクト。

# 戻り値

  * `Tuple{NamedTuple{(:prior, :posterior, :predictive),Tuple{NamedTuple{(:α, :β, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64}}},NamedTuple{(:α, :β, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64}}},NamedTuple{(:μ, :σ, :ξ, :n, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64},Vector{Int64},Vector{Vector{Float64}}}}}}}`: 事前、事後、予測分布のパラメータを含むタプル。
