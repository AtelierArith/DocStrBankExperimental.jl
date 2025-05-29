```
Optimisers.init(rule::RuleType, parameters) -> state
```

与えられた最適化ルールの初期状態とパラメータの配列を設定します。これと [`apply!`](@ref Optimisers.apply!) は、新しい最適化ルールが定義しなければならない2つの関数です。

# 例

```jldoctest
julia> Optimisers.init(Descent(), Float32[1,2,3])  # は `nothing`

julia> Optimisers.init(Momentum(), [1.0, 2.0])
2-element Vector{Float64}:
 0.0
 0.0
```
