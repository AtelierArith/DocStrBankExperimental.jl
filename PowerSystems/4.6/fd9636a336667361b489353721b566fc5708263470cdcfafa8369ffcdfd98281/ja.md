```julia
get_decremental_offer_curves(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, TimeSeries.TimeArray}

```

`StaticInjection`デバイスの`MarketBidCost`に対する`decremental_offer_curves`を取得します。このフィールドが時系列である場合、ユーザーは`start_time`と`len`を指定でき、関数は`Float64`の`TimeArray`を返します。フィールドが時系列でない場合、関数は単一の`Float64`または`Nothing`を返します。
