```julia
get_incremental_variable_cost(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey, TimeSeries.TimeArray}

```

`StaticInjection`デバイスの`MarketBidCost`に対する変動コスト入札を取得します。関連するフィールド（`incremental_offer_curves`、`initial_input`、`no_load_cost`）のいずれかが時系列である場合、ユーザーは`start_time`と`len`を指定でき、関数は`CostCurve`の`TimeArray`を返します。フィールドが時系列でない場合、関数は単一の`CostCurve`を返します。
