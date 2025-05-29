```julia
Deterministic(
    src::InfrastructureSystems.Deterministic,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

既存のインスタンスからデータを共有するDeterministicを構築します。

これは、コンポーネントが2つの異なる属性に対して同じ時系列データを使用する必要がある場合に便利です。

# 例

```julia
resolution = Dates.Hour(1)
data = Dict(
    DateTime("2020-01-01T00:00:00") => ones(24),
    DateTime("2020-01-01T01:00:00") => ones(24),
)
# 最初の属性のためのDeterministicを定義
forecast_max_active_power = Deterministic(
    "max_active_power",
    data,
    resolution,
    scaling_factor_multiplier = get_max_active_power,
)
add_time_series!(sys, generator, forecast_max_active_power)
# 2番目の属性のために時系列を再利用
forecast_max_reactive_power = Deterministic(
    forecast_max_active_power,
    "max_reactive_power"
    scaling_factor_multiplier = get_max_reactive_power,
)
add_time_series!(sys, generator, forecast_max_reactive_power)
```
