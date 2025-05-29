```
mutable struct RenewableDispatch <: RenewableGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    reactive_power_limits::Union{Nothing, MinMax}
    power_factor::Float64
    operation_cost::Union{RenewableGenerationCost, MarketBidCost}
    base_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

出力を制限して電力システムの制約を満たすことができる再生可能（例：風力または太陽光）発電機。

これらの発電機は、利用可能な電力の一部を積極的に制限することによって、上向きの予備市場にも参加できます（その基準は[`max_active_power` 時系列](@ref ts_data)に基づきます）。例としては、制限を許可するPPAを持つユーティリティ規模の風力または太陽光発電機が含まれます。制限できないまたは必ず受け取る再生可能エネルギーについては、[`RenewableNonDispatch`](@ref)を参照してください。

再生可能発電機には`max_active_power`パラメータはなく、代わりに[`get_max_active_power()`](@ref get_max_active_power(d::T) where {T <: RenewableGen})を呼び出す際に計算されます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます
  * `bus::ACBus`: このコンポーネントが接続されているバス
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これはソルバーによって使用される初期の出発点として使用される場合とそうでない場合があります
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）、一部の生産コストモデリングシミュレーションで使用されます。負荷フローでリアクティブパワーを設定するには、`power_factor`を使用します
  * `rating::Float64`: ユニットの最大出力電力定格（MVA）、検証範囲: `(0, nothing)`
  * `prime_mover_type::PrimeMovers`: EIA 923に基づくプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大リアクティブパワー制限、一部の生産コストモデルシミュレーションおよびユニットが[`PV`](@ref acbustypes_list)バスに接続されている場合の電力フローで使用されます。該当しない場合は`nothing`に設定します
  * `power_factor::Float64`: パワーファクター[0, 1]設定値、一部の生産コストモデリングおよびユニットが[`PQ`](@ref acbustypes_list)バスに接続されている場合の負荷フローで使用されます、検証範囲: `(0, 1)`
  * `operation_cost::Union{RenewableGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref)の発電
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準電力（MVA）、検証範囲: `(0, nothing)`
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）対応する動的注入デバイス
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するためのユーザー用の[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
