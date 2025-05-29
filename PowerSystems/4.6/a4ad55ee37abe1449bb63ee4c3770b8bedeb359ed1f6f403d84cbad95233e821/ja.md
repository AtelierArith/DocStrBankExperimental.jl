```
mutable struct ExponentialLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    α::Float64
    β::Float64
    base_power::Float64
    max_active_power::Float64
    max_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

電圧依存型の [ZIP load](@ref Z) で、動的モデリングに最も一般的に使用されます。

`ExponentialLoad` は、P = P0 * V^α としてアクティブパワーをモデル化し、Q = Q0 * V^β としてリアクティブパワーをモデル化します。ここで、指数 α と β は電圧依存性を制御します。ZIPモデルの代替の三部構成については、[`StandardLoad`](@ref) を参照してください。電圧依存性のないよりシンプルな負荷モデルについては、[`PowerLoad`](@ref) を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: アクティブパワー係数、P0 (MW)
  * `reactive_power::Float64`: リアクティブパワー係数、Q0 (MVAR)
  * `α::Float64`: アクティブパワーの電圧依存性に関連する指数。0 = 定常電力のみ、1 = 定常電流のみ、2 = 定常インピーダンスのみ、検証範囲: `(0, nothing)`
  * `β::Float64`: リアクティブパワーの電圧依存性に関連する指数。0 = 定常電力のみ、1 = 定常電流のみ、2 = 定常インピーダンスのみ、検証範囲: `(0, nothing)`
  * `base_power::Float64`: [パー・ユニット化](@ref per_unit)のための基準電力 (MVA)、検証範囲: `(0, nothing)`
  * `max_active_power::Float64`: この負荷が要求できる最大アクティブパワー (MW)
  * `max_reactive_power::Float64`: この負荷が要求できる最大リアクティブパワー (MVAR)
  * `services::Vector{Service}`: (デフォルト: `Device[]`) このデバイスが貢献するサービス
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (デフォルト: `nothing`) 対応する動的注入デバイス
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra dictionary](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl の内部参照
