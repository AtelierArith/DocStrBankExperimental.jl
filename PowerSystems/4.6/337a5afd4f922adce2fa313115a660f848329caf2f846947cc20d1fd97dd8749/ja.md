```
mutable struct HydroEnergyReservoir <: HydroGen
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
    storage_capacity::Float64
    inflow::Float64
    initial_storage::Float64
    operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}
    storage_target::Float64
    conversion_factor::Float64
    status::Bool
    time_at_status::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

上部貯水池を持つ水力発電機で、エネルギー貯蔵と運用の柔軟性を提供します。

ポンプ貯水式水力発電機については、[`HydroPumpedStorage`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これはソルバーによって初期の出発点として使用される場合とされない場合があります。
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）、検証範囲：`reactive_power_limits`
  * `rating::Float64`: ユニットの最大出力パワー定格（MVA）、検証範囲：`(0, nothing)`
  * `prime_mover_type::PrimeMovers`: EIA 923に基づくプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています。
  * `active_power_limits::MinMax`: 最小および最大の安定アクティブパワーレベル（MW）
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大のリアクティブパワー制限。該当しない場合は`Nothing`に設定します。
  * `ramp_limits::Union{Nothing, UpDown}`: MW/分での立ち上げおよび立ち下げ制限、検証範囲：`(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: 最小立ち上げおよび最小立ち下げ時間制限（時間）、検証範囲：`(0, nothing)`
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準パワー（MVA）、検証範囲：`(0, nothing)`
  * `storage_capacity::Float64`: 貯水池の最大貯蔵容量（単位はp.u-hrまたはm^3）、検証範囲：`(0, nothing)`
  * `inflow::Float64`: 貯水池への基準流入（単位はp.u.またはm^3/hr）、検証範囲：`(0, nothing)`
  * `initial_storage::Float64`: 貯水池の初期貯蔵容量（単位はp.u-hrまたはm^3）、検証範囲：`(0, nothing)`
  * `operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}`: （デフォルト：`HydroGenerationCost(nothing)`）発電の[`OperationalCost`](@ref)。
  * `storage_target::Float64`: （デフォルト：`1.0`）シミュレーション終了時の貯蔵容量の割合としての貯蔵目標。
  * `conversion_factor::Float64`: （デフォルト：`1.0`）流量/体積からエネルギーへの変換係数：m^3 -> p.u-hr。
  * `status::Bool`: （デフォルト：`false`）シミュレーション開始時の初期コミットメント条件（`true` = オンまたは`false` = オフ）。
  * `time_at_status::Float64`: （デフォルト：`INFINITE_TIME`）ジェネレーターがオンまたはオフであった時間（例：`Hours(6)`）、`status`によって示されます。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照。
