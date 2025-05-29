```julia
get_services_bid(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost,
    service::PowerSystems.Service;
    start_time,
    len
) -> TimeSeries.TimeArray

```

`StaticInjection`デバイスと`MarketBidCost`を持つサービス入札の時系列データを返します。ユーザーは`start_time`と`len`を指定でき、関数は`CostCurve`の`TimeArray`を返します。
