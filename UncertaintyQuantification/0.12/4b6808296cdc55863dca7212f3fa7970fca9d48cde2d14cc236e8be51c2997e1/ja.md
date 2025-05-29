```
ProbabilityBox{T}(p::AbstractVector{Interval}, name::Symbol)
```

`Interval`の`Vector`からProbabilityBoxを定義し、名前は`UnivariateDistribution` `T`です。パラメータの数と順序は、Distributions.jlの関連する分布のパラメータと一致する必要があります。

# 例

```jldoctest
julia>  ProbabilityBox{Uniform}([Interval(1.75, 1.83, :a), Interval(1.77, 1.85, :b)], :l)
ProbabilityBox{Uniform}(Interval[Interval(1.75, 1.83, :a), Interval(1.77, 1.85, :b)], :l, 1.75, 1.85)
```

```jldoctest
julia>  ProbabilityBox{Normal}([Interval(0, 1, :μ), Interval(0.1, 1, :σ)], :x)
ProbabilityBox{Normal}(Interval[Interval(0, 1, :μ), Interval(0.1, 1, :σ)], :x, -Inf, Inf)
```
