```julia
get_shut_down(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Float64, TimeSeries.TimeArray}

```

`StaticInjection`デバイスの`MarketBidCost`に対するシャットダウンコストデータを取得します。このフィールドが時系列である場合、ユーザーは`start_time`と`len`を指定でき、関数は`Float64`の`TimeArray`を返します。フィールドが時系列でない場合、関数は単一の`Float64`を返します。
