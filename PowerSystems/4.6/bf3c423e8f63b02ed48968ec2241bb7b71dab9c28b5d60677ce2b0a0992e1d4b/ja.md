```
mutable struct PowerLoad <: StaticLoad
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    base_power::Float64
    max_active_power::Float64
    max_reactive_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

静的な[static](@ref S)電力負荷で、主に電力フローや運用最適化などの運用モデルで使用されます。

この負荷は、電力フローシミュレーションのために`active_power`で設定された一定の電力を消費します。または、運用シミュレーションのための`max_active_power`の時系列です。需要応答プログラムを通じて負荷中断を補償できる負荷については、[`InterruptiblePowerLoad`](@ref)を参照してください。 [dynamics](@ref D)モデリングで使用される電圧依存型負荷については、[`StandardLoad`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス
  * `active_power::Float64`: 初期定常状態の有効電力需要（MW）
  * `reactive_power::Float64`: 初期定常状態の無効電力需要（MVAR）
  * `base_power::Float64`: [単位化](@ref per_unit)のための基準電力（MVA）、検証範囲: `(0, nothing)`
  * `max_active_power::Float64`: この負荷が要求できる最大有効電力（MW）
  * `max_reactive_power::Float64`: この負荷が要求できる最大無効電力（MVAR）
  * `services::Vector{Service}`: (デフォルト: `Device[]`) このデバイスが貢献するサービス
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (デフォルト: `nothing`) 対応する動的注入デバイス
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
