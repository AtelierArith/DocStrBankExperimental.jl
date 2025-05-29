```
invlink(d::Distribution, y)
```

分布 `d` の制約付きから非制約付きの双射を使用して変換された値 `y` に対して逆変換を実行します。

`invlink(d, link(d, x)) = x` が成り立つべきです。

参照: [`link`](@ref).

# 例

```jldoctest
julia> using Bijectors

julia> d = LogNormal()    # サポートは (0, Inf)
LogNormal{Float64}(μ=0.0, σ=1.0)

julia> link(LogNormal(), 1.0)   # 対数変換を使用
0.0

julia> invlink(LogNormal(), 0.0)
1.0
```
