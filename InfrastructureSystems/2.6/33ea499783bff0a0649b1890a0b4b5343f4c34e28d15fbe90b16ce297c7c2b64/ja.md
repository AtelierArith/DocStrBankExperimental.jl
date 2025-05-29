```julia
SingleTimeSeries(
    src::InfrastructureSystems.SingleTimeSeries,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.SingleTimeSeries

```

既存のインスタンスからデータを共有するSingleTimeSeriesを構築します。

これは、コンポーネントが2つの異なる属性に対して同じ時系列データを使用する必要がある場合に便利です。
