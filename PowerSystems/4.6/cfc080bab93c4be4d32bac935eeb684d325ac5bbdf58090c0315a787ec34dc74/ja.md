```
mutable struct InterconnectingConverter <: StaticInjection
    name::String
    available::Bool
    bus::ACBus
    dc_bus::DCBus
    active_power::Float64
    rating::Float64
    active_power_limits::MinMax
    base_power::Float64
    dc_current::Float64
    max_dc_current::Float64
    loss_function::Union{LinearCurve, QuadraticCurve}
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

ACBusからDCBusへの電力変換のための相互接続電力コンバータ（IPC）

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます
  * `bus::ACBus`: このコンバータのAC側のバス
  * `dc_bus::DCBus`: このコンバータのDC側のバス
  * `active_power::Float64`: DC側の有効電力（MW）、検証範囲：`active_power_limits`
  * `rating::Float64`: コンバータの最大出力電力定格（MVA）、検証範囲：`(0, nothing)`
  * `active_power_limits::MinMax`: 最小および最大の安定した有効電力レベル（MW）
  * `base_power::Float64`: コンバータの基準電力（MVA）、検証範囲：`(0, nothing)`
  * `dc_current::Float64`: （デフォルト：`0.0`）コンバータのDC電流（A）
  * `max_dc_current::Float64`: （デフォルト：`1e8`）最大安定DC電流制限（A）
  * `loss_function::Union{LinearCurve, QuadraticCurve}`: （デフォルト：`LinearCurve(0.0)`）コンバータ電流に関する線形または二次損失関数
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）対応する動的注入デバイス
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
