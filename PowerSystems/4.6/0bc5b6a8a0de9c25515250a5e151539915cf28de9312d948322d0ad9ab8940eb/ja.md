```
mutable struct InterruptiblePowerLoad <: ControllableLoad
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    max_active_power::Float64
    max_reactive_power::Float64
    base_power::Float64
    operation_cost::Union{LoadCost, MarketBidCost}
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

要求された需要に対する一時的または継続的な中断を補償できる[静的](@ref S)電力負荷。

これらの負荷は、運用最適化に最も一般的に使用され、需要応答プログラムに登録された大規模な商業および産業顧客をモデル化するために使用できます。この負荷には、他のシステムのニーズを満たすために削減できるターゲット需要プロファイル（運用シミュレーションのための[`max_active_power`時系列](@ref ts_data）によって設定）が含まれています。需要応答のための運用コストがないより単純な負荷については、[`PowerLoad`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス
  * `active_power::Float64`: 初期定常状態の有効電力需要（MW）
  * `reactive_power::Float64`: 初期定常状態の無効電力需要（MVAR）
  * `max_active_power::Float64`: この負荷が要求できる最大有効電力（MW）
  * `max_reactive_power::Float64`: この負荷が要求できる最大無効電力（MVAR）
  * `base_power::Float64`: [単位化](@ref per_unit)のための基準電力（MVA）、検証範囲: `(0, nothing)`
  * `operation_cost::Union{LoadCost, MarketBidCost}`: 負荷を中断するための[`OperationalCost`](@ref)
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）対応する動的注入デバイス
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
