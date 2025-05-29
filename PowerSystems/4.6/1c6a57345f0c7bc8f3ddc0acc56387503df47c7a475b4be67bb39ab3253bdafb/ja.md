```
mutable struct StandardLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    base_power::Float64
    constant_active_power::Float64
    constant_reactive_power::Float64
    impedance_active_power::Float64
    impedance_reactive_power::Float64
    current_active_power::Float64
    current_reactive_power::Float64
    max_constant_active_power::Float64
    max_constant_reactive_power::Float64
    max_impedance_active_power::Float64
    max_impedance_reactive_power::Float64
    max_current_active_power::Float64
    max_current_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

電圧依存型の [ZIP load](@ref Z) は、動的モデリングで最も一般的に使用されます。

`StandardLoad` は、ZIPを3つの部分に分解します：Z（定常インピーダンス）、I（定常電流）、P（定常電力）。これは、`P = P_P * V^0 + P_I * V^1 + P_Z * V^2`（有効電力）および `Q = Q_P * V^0 + Q_I * V^1 + Q_Z * V^2`（無効電力）に従います。（電圧Vはパーユニットで表されます。）

ZIPモデルの代替指数形式については、[`ExponentialLoad`](@ref)を参照してください。電圧依存性のないよりシンプルな負荷モデルについては、[`PowerLoad`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `base_power::Float64`: 負荷の基準電力（MVA）で、[パーユニット化](@ref per_unit)のための検証範囲は `(0, nothing)` です。
  * `constant_active_power::Float64`: （デフォルト：`0.0`）定常有効電力需要（MW）（P_P）。
  * `constant_reactive_power::Float64`: （デフォルト：`0.0`）定常無効電力需要（MVAR）（Q_P）。
  * `impedance_active_power::Float64`: （デフォルト：`0.0`）定常インピーダンス負荷の有効電力係数（MW）（P_Z）。
  * `impedance_reactive_power::Float64`: （デフォルト：`0.0`）定常インピーダンス負荷の無効電力係数（MVAR）（Q_Z）。
  * `current_active_power::Float64`: （デフォルト：`0.0`）定常電流負荷の有効電力係数（MW）（P_I）。
  * `current_reactive_power::Float64`: （デフォルト：`0.0`）定常電流負荷の無効電力係数（MVAR）（Q_I）。
  * `max_constant_active_power::Float64`: （デフォルト：`0.0`）定常電力負荷によって引き出される最大有効電力（MW）。
  * `max_constant_reactive_power::Float64`: （デフォルト：`0.0`）定常電力負荷によって引き出される最大無効電力（MVAR）。
  * `max_impedance_active_power::Float64`: （デフォルト：`0.0`）定常インピーダンス負荷によって引き出される最大有効電力（MW）。
  * `max_impedance_reactive_power::Float64`: （デフォルト：`0.0`）定常インピーダンス負荷によって引き出される最大無効電力（MVAR）。
  * `max_current_active_power::Float64`: （デフォルト：`0.0`）定常電流負荷によって引き出される最大有効電力（MW）。
  * `max_current_reactive_power::Float64`: （デフォルト：`0.0`）定常電流負荷によって引き出される最大無効電力（MVAR）。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための [*ext*ra dictionary](@ref additional_fields)（例：緯度と経度）。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl の内部参照。
