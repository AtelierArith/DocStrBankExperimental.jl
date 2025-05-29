```julia
reaction!(
    f,
    u,
    node,
    data,
    _::Type{ChargeTransport.InEquilibrium}
)

```

平衡状態の場合の反応、すなわち生成と再結合は考慮されません。
