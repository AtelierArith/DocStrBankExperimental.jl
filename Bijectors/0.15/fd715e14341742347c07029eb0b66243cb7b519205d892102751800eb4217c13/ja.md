```
link(d::Distribution, x)
```

入力 `x` を分布 `d` の制約付きから非制約付きの双射を使用して変換します。

関連項目: [`invlink`](@ref).

# 例

```jldoctest
julia> using Bijectors

julia> d = LogNormal()   # サポートは (0, Inf)
LogNormal{Float64}(μ=0.0, σ=1.0)

julia> b = bijector(d)   # 対数関数が非制約空間に変換します
(::Base.Fix1{typeof(broadcast), typeof(log)}) (generic function with 1 method)

julia> b(1.0)
0.0

julia> link(LogNormal(), 1.0)
0.0
```
