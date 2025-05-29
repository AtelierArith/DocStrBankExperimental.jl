```
minimise(network::AbstractApproximator, x::AbstractMatrix;
    min_decision=nothing, max_decision=nothing,
)
```

与えられたデータポイント `x::AbstractMatrix` に対して `network::AbstractApproximator` の最小化器を pmap を使用して見つけます。
