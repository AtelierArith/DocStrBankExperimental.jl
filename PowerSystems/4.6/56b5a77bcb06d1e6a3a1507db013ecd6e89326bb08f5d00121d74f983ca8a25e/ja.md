```julia
mutable struct MarketBidCost <: PowerSystems.OperationalCost
```

  * `no_load_cost::Union{Nothing, Float64, InfrastructureSystems.TimeSeriesKey}`: 無負荷コスト
  * `start_up::Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesKey}`: ユニットがシャットダウン後に冷却される際の熱サイクルの異なる段階での起動コスト（例：*hot*、*warm*、または*cold*スタート）。ウォームは一部の市場では中間とも呼ばれます。起動コストが1つだけの場合は単一の値も受け入れ可能です。
  * `shut_down::Union{Float64, InfrastructureSystems.TimeSeriesKey}`: シャットダウンコスト
  * `incremental_offer_curves::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}`: 売却オファーカーブデータで、`PiecewiseStepData`の時系列または[`CostCurve`](@ref)の[`PiecewiseIncrementalCurve`](@ref)であることができます。
  * `decremental_offer_curves::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}`: 購入オファーカーブデータで、`PiecewiseStepData`の時系列または[`CostCurve`](@ref)の[`PiecewiseIncrementalCurve`](@ref)であることができます。
  * `incremental_initial_input::Union{Nothing, InfrastructureSystems.TimeSeriesKey}`: 増分*オファー*カーブに時系列を使用する場合、これは`initial_input`を表す`Float64`の時系列です。
  * `decremental_initial_input::Union{Nothing, InfrastructureSystems.TimeSeriesKey}`: 減分*オファー*カーブに時系列を使用する場合、これは`initial_input`を表す`Float64`の時系列です。
  * `ancillary_service_offers::Vector{PowerSystems.Service}`: 補助サービスの入札

```
MarketBidCost(no_load_cost, start_up, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
MarketBidCost(; no_load_cost, start_up, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
MarketBidCost(no_load_cost, start_up::Real, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
```

エネルギーおよび補助サービスの市場入札の運用コストであり、任意の資産に対応しています。需要と発電側をサポートするほとんどの米国市場の入札メカニズムと互換性があります。
