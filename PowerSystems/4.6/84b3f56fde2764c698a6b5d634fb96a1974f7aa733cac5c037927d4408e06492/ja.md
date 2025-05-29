```
mutable struct EnergyReservoirStorage <: Storage
    name::String
    available::Bool
    bus::ACBus
    prime_mover_type::PrimeMovers
    storage_technology_type::StorageTech
    storage_capacity::Float64
    storage_level_limits::MinMax
    initial_storage_capacity_level::Float64
    rating::Float64
    active_power::Float64
    input_active_power_limits::MinMax
    output_active_power_limits::MinMax
    efficiency::NamedTuple{(:in, :out), Tuple{Float64, Float64}}
    reactive_power::Float64
    reactive_power_limits::Union{Nothing, MinMax}
    base_power::Float64
    operation_cost::Union{StorageCost, MarketBidCost}
    conversion_factor::Float64
    storage_target::Float64
    cycle_limits::Int
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

エネルギー貯蔵装置は、一般的なエネルギー貯蔵池としてモデル化されています。

これは、貯蔵ユニットの物理的ダイナミクスを無視して、平均効率損失を伴う貯蔵の充電と放電をモデル化するのに適しています。このアプローチでは、さまざまなエネルギー貯蔵タイプや化学をモデル化できます。揚水発電所については、代わりに[`HydroPumpedStorage`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `prime_mover_type::PrimeMovers`: EIA 923に従ったプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています。
  * `storage_technology_type::StorageTech`: EIA 923に補完的な貯蔵技術。オプションは[こちら](@ref storagetech_list)にリストされています。
  * `storage_capacity::Float64`: 最大貯蔵容量（バッテリーの場合はMWh、または水素の場合はリットルなどの単位で表される可能性があります）、検証範囲: `(0, nothing)`
  * `storage_level_limits::MinMax`: 最小および最大の許容貯蔵レベル [0, 1]。これは、バッテリーサイクリングの充電状態制限など、デレートやその他の制限をモデル化するために使用できます。検証範囲: `(0, 1)`
  * `initial_storage_capacity_level::Float64`: `storage_capacity`の比率 [0, 1.0] としての初期貯蔵容量レベル。検証範囲: `(0, 1)`
  * `rating::Float64`: ユニットの最大出力電力定格 (MVA)。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデルの場合、これはソルバーの初期スタートポイントとして使用される場合とされない場合があります。
  * `input_active_power_limits::MinMax`: 入力アクティブパワー（すなわち、充電）の最小および最大制限。検証範囲: `(0, nothing)`
  * `output_active_power_limits::MinMax`: 出力アクティブパワー（すなわち、放電）の最小および最大制限。検証範囲: `(0, nothing)`
  * `efficiency::NamedTuple{(:in, :out), Tuple{Float64, Float64}}`: 貯蔵システムの平均効率 [0, 1] `in`（充電/充填）および `out`（放電/消費）。検証範囲: `(0, 1)`
  * `reactive_power::Float64`: ユニットの初期無効電力設定値（MVAR）。検証範囲: `reactive_power_limits`
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大の無効電力制限。該当しない場合は`Nothing`に設定します。
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準電力 (MVA)。検証範囲: `(0, nothing)`
  * `operation_cost::Union{StorageCost, MarketBidCost}`: （デフォルト: `StorageCost(nothing)`）貯蔵の[`OperationalCost`](@ref)。
  * `conversion_factor::Float64`: （デフォルト: `1.0`）`storage_capacity`をMWhに変換するための変換係数。1.0と異なる場合。例えば、X MWh/リットルの水素。
  * `storage_target::Float64`: （デフォルト: `0.0`）シミュレーションの終了時の貯蔵目標としての貯蔵容量の比率。
  * `cycle_limits::Int`: （デフォルト: `1e4`）年間の最大サイクル数。
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)。例えば、緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jlの内部参照。
