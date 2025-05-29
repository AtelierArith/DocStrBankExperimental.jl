```
mutable struct HydroPumpedStorage <: HydroGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    base_power::Float64
    prime_mover_type::PrimeMovers
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    time_limits::Union{Nothing, UpDown}
    rating_pump::Float64
    active_power_limits_pump::MinMax
    reactive_power_limits_pump::Union{Nothing, MinMax}
    ramp_limits_pump::Union{Nothing, UpDown}
    time_limits_pump::Union{Nothing, UpDown}
    storage_capacity::UpDown
    inflow::Float64
    outflow::Float64
    initial_storage::UpDown
    storage_target::UpDown
    operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}
    pump_efficiency::Float64
    conversion_factor::Float64
    status::PumpHydroStatus
    time_at_status::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

揚水発電所を持つ水力発電機。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これはソルバーによって初期の出発点として使用される場合とされない場合があります。
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）。
  * `rating::Float64`: ユニットの最大出力パワー定格（MVA）、検証範囲: `(0, nothing)`。
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準電力（MVA）、検証範囲: `(0, nothing)`。
  * `prime_mover_type::PrimeMovers`: EIA 923に基づくプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています。
  * `active_power_limits::MinMax`: 最小および最大の安定アクティブパワーレベル（MW）、検証範囲: `(0, nothing)`。
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大のリアクティブパワー制限。該当しない場合は`Nothing`に設定します。
  * `ramp_limits::Union{Nothing, UpDown}`: MW/minのラップアップおよびラップダウン制限、検証範囲: `(0, nothing)`。
  * `time_limits::Union{Nothing, UpDown}`: 最小アップおよび最小ダウン時間制限（時間単位）、検証範囲: `(0, nothing)`。
  * `rating_pump::Float64`: ポンプの最大電力引き出し（MVA）、検証範囲: `(0, nothing)`。
  * `active_power_limits_pump::MinMax`:
  * `reactive_power_limits_pump::Union{Nothing, MinMax}`:
  * `ramp_limits_pump::Union{Nothing, UpDown}`: ポンプのMW/minのラップアップおよびラップダウン制限、検証範囲: `(0, nothing)`。
  * `time_limits_pump::Union{Nothing, UpDown}`: ポンプの最小アップおよび最小ダウン時間制限（時間単位）、検証範囲: `(0, nothing)`。
  * `storage_capacity::UpDown`: 上下の貯水池の最大貯蔵容量（単位はp.u-hrまたはm^3）、検証範囲: `(0, nothing)`。
  * `inflow::Float64`: 上部貯水池への基準流入（単位はp.u.またはm^3/hr）、検証範囲: `(0, nothing)`。
  * `outflow::Float64`: 下部貯水池からの基準流出（単位はp.u.またはm^3/hr）、検証範囲: `(0, nothing)`。
  * `initial_storage::UpDown`: 上下の貯水池の初期貯蔵容量（単位はp.u-hrまたはm^3）、検証範囲: `(0, nothing)`。
  * `storage_target::UpDown`: （デフォルト: `(up=1.0, down=1.0)`）シミュレーション終了時の上部貯水池の貯蔵目標（貯蔵容量の比率）。
  * `operation_cost::Union{HydroGenerationCost, StorageCost, MarketBidCost}`: （デフォルト: `HydroGenerationCost(nothing)`）発電の[`OperationalCost`](@ref)。
  * `pump_efficiency::Float64`: （デフォルト: `1.0`）ポンプ効率 [0, 1.0]、検証範囲: `(0, 1)`。
  * `conversion_factor::Float64`: （デフォルト: `1.0`）流量/体積からエネルギーへの変換係数: m^3 -> p.u-hr。
  * `status::PumpHydroStatus`: （デフォルト: `PumpHydroStatus.OFF`）シミュレーション開始時の初期コミットメント条件（`PumpHydroStatus.PUMP`、`PumpHydroStatus.GEN`、または`PumpHydroStatus.OFF`）。
  * `time_at_status::Float64`: （デフォルト: `INFINITE_TIME`）ジェネレーターが生成、ポンプ、またはオフであった時間（例：`Hours(6)`）、`status`によって示されます。
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)（例：緯度と経度）。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照。
