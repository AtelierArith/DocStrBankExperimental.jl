```julia
set_start_up!(
    value::PowerSystems.MarketBidCost,
    val::Real
) -> NamedTuple{(:hot, :warm, :cold), <:Tuple{Any, Float64, Float64}}

```

マルチスタートではないスタートアップを設定するための補助メソッド
