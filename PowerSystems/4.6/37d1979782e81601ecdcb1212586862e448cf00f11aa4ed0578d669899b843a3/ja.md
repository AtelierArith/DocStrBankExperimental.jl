```
mutable struct HybridSystem <: StaticInjectionSubsystem
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    base_power::Float64
    operation_cost::MarketBidCost
    thermal_unit::Union{Nothing, ThermalGen}
    electric_load::Union{Nothing, ElectricLoad}
    storage::Union{Nothing, Storage}
    renewable_unit::Union{Nothing, RenewableGen}
    interconnection_impedance::ComplexF64
    interconnection_rating::Union{Nothing, Float64}
    input_active_power_limits::Union{Nothing, MinMax}
    output_active_power_limits::Union{Nothing, MinMax}
    reactive_power_limits::Union{Nothing, MinMax}
    interconnection_efficiency::Union{
        Nothing,
        NamedTuple{(:in, :out), Tuple{Float64, Float64}},
    }
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

再生可能エネルギー発電、負荷、熱発電および/またはエネルギー貯蔵の組み合わせを含むハイブリッドシステム。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `status::Bool`: シミュレーション開始時の初期コミットメント条件（`true` = オンまたは`false` = オフ）。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。パワーフローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これは使用されるソルバーによって初期の出発点として使用される場合とされない場合があります。
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）。
  * `base_power::Float64`: ユニットのベースパワー（MVA）で、単位化のために一般的に`rating`と同じです。
  * `operation_cost::MarketBidCost`: 操作のための市場入札コスト、[`MarketBidCost`](@ref)。
  * `thermal_unit::Union{Nothing, ThermalGen}`: スーパタイプ[`ThermalGen`](@ref)を持つ熱発電機。
  * `electric_load::Union{Nothing, ElectricLoad}`: スーパタイプ[`ElectricLoad`](@ref)を持つ負荷。
  * `storage::Union{Nothing, Storage}`: スーパタイプ[`Storage`](@ref)を持つエネルギー貯蔵システム。
  * `renewable_unit::Union{Nothing, RenewableGen}`: スーパタイプ[`RenewableGen`](@ref)を持つ再生可能発電機。
  * `interconnection_impedance::ComplexF64`: ハイブリッドシステムとグリッド間のインピーダンス（通常はp.u.）。
  * `interconnection_rating::Union{Nothing, Float64}`: 送電ネットワークとのハイブリッドシステムの接続の最大定格（MVA）。
  * `input_active_power_limits::MinMax`: 最小および最大の安定した入力アクティブパワーレベル（MW）。
  * `output_active_power_limits::MinMax`: 最小および最大の安定した出力アクティブパワーレベル（MW）。
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大のリアクティブパワー制限（MVAR）。該当しない場合は`Nothing`に設定します。
  * `interconnection_efficiency::Union{Nothing, NamedTuple{(:in, :out), Tuple{Float64, Float64}},}`: グリッド接続での効率[0, 1.0]、共通のDC側変換の損失をモデル化するための`in`および`out`。
  * `services::Vector{Service}`: （オプション）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （オプション）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （オプション）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
