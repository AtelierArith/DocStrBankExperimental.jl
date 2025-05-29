```
mutable struct MonitoredLine <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    b::FromTo
    flow_limits::FromTo_ToFrom
    rating::Float64
    angle_limits::MinMax
    g::FromTo
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

システムオペレーターによって指定された追加の電力フロー制約を持つAC送電線で、線の熱限界よりも制限が厳しいです。

例えば、モニタリングされたラインは、ネットワーク内の他の場所での非常事態に従ってラインフローを制限するために使用できます。`flow_limits`パラメータを参照してください。モニタリングが必要ない場合は、[`Line`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: ライン上のアクティブ電力フローの初期条件（MW）。
  * `reactive_power_flow::Float64`: ライン上のリアクティブ電力フローの初期条件（MVAR）。
  * `arc::Arc`: バスから別のバスへのこのラインを定義する[`Arc`](@ref)。
  * `r::Float64`: puでの抵抗（[`SYSTEM_BASE`](@ref per_unit））、検証範囲: `(0, 4)`。
  * `x::Float64`: puでのリアクタンス（[`SYSTEM_BASE`](@ref per_unit））、検証範囲: `(0, 4)`。
  * `b::FromTo`: puでのシャントサスペクタンス（[`SYSTEM_BASE`](@ref per_unit））、ラインの`from`および`to`の両端で指定されます。これらは通常同じ値でモデル化され、検証範囲: `(0, 2)`。
  * `flow_limits::FromTo_ToFrom`: ライン上の最小および最大許容フロー（MVA）、`rating`で定義された熱定格と異なる場合。
  * `rating::Float64`: 熱定格（MVA）。トランスを通るフローは-`rating`と`rating`の間でなければなりません。ラインを`System`に接続する前に定義する場合、`rating`は接続される`System`の基準電力を使用してpu（[`SYSTEM_BASE`](@ref per_unit））でなければなりません。
  * `angle_limits::MinMax`: 最小および最大角度制限（ラジアン）、検証範囲: `(-1.571, 1.571)`。
  * `g::FromTo`: （デフォルト: `(from=0.0, to=0.0)`）puでのシャントコンダクタンス（[`SYSTEM_BASE`](@ref per_unit））、ラインの`from`および`to`の両端で指定されます。これらは通常同じ値でモデル化され、検証範囲: `(0, 100)`。
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
