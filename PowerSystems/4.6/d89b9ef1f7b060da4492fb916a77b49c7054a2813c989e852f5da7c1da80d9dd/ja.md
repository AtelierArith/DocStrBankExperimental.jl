```
mutable struct Line <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    b::FromTo
    rating::Float64
    angle_limits::MinMax
    g::FromTo
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

AC送電線

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、または切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます
  * `active_power_flow::Float64`: 線上の有効電力フローの初期条件（MW）
  * `reactive_power_flow::Float64`: 線上の無効電力フローの初期条件（MVAR）
  * `arc::Arc`: バスから別のバスへのこの線を定義する [`Arc`](@ref)
  * `r::Float64`: pu における抵抗（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲: `(0, 4)`
  * `x::Float64`: pu におけるリアクタンス（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲: `(0, 4)`
  * `b::FromTo`: pu におけるシャントの感受性（[`SYSTEM_BASE`](@ref per_unit)）、線の `from` および `to` の両端で指定されます。これらは通常同じ値でモデル化され、検証範囲: `(0, 100)`
  * `rating::Float64`: 熱定格（MVA）。線上のフローは -`rating` と `rating` の間でなければなりません。線を `System` に接続する前に定義する場合、`rating` は接続される `System` の基準電力を使用して pu（[`SYSTEM_BASE`](@ref per_unit)）でなければなりません
  * `angle_limits::MinMax`: 最小および最大角度制限（ラジアン）、検証範囲: `(-1.571, 1.571)`
  * `g::FromTo`: （デフォルト: `(from=0.0, to=0.0)`）pu におけるシャントの導電率（[`SYSTEM_BASE`](@ref per_unit)）、線の `from` および `to` の両端で指定されます。これらは通常同じ値でモデル化され、検証範囲: `(0, 100)`
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための [*ext*ra 辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl の内部参照
