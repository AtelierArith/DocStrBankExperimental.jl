```julia
get_start_up(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, TimeSeries.TimeArray}

```

`StaticInjection`デバイスの`MarketBidCost`に対するスタートアップコストデータを取得します。このフィールドが時系列である場合、ユーザーは`start_time`と`len`を指定でき、関数は`StartUpStages`の`TimeArray`を返します。フィールドが時系列でない場合、関数は単一の`StartUpStages`を返します。
