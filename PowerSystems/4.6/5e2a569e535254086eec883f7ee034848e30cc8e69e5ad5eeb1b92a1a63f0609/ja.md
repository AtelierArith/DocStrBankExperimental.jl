```
mutable struct HydroDispatch <: HydroGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    time_limits::Union{Nothing, UpDown}
    base_power::Float64
    operation_cost::Union{HydroGenerationCost, MarketBidCost}
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

貯水池のない水力発電機で、河川流量水力発電のモデル化に適しています。

上部貯水池を持つ水力発電機については、[`HydroEnergyReservoir`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これは使用されるソルバーによって初期の出発点として使用される場合とされない場合があります。
  * `reactive_power::Float64`: ユニットの初期無効電力設定値（MVAR）、検証範囲：`reactive_power_limits`
  * `rating::Float64`: ユニットの最大出力電力定格（MVA）、検証範囲：`(0, nothing)`
  * `prime_mover_type::PrimeMovers`: EIA 923に従ったプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています。
  * `active_power_limits::MinMax`: 最小および最大の安定アクティブパワーレベル（MW）、検証範囲：`(0, nothing)`
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大の無効電力制限。該当しない場合は`Nothing`に設定します。
  * `ramp_limits::Union{Nothing, UpDown}`: MW/分での立ち上げおよび立ち下げ制限、検証範囲：`(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: 最小立ち上げおよび最小立ち下げ時間制限（時間）、検証範囲：`(0, nothing)`
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準電力（MVA）、検証範囲：`(0, nothing)`
  * `operation_cost::Union{HydroGenerationCost, MarketBidCost}`: （デフォルト：`HydroGenerationCost(nothing)`）発電の[`OperationalCost`](@ref)。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
