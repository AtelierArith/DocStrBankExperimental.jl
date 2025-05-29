```
mutable struct PhaseShiftingTransformer <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    primary_shunt::Float64
    tap::Float64
    α::Float64
    rating::Union{Nothing, Float64}
    phase_angle_limits::MinMax
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

2つのバス間の位相角を調整してシステム内の有効電力フローを制御する位相シフトトランス。

このモデルは、トランスの高電圧側にインピーダンスがあると仮定した等価回路を使用します。このモデルは、鉄損失と励磁リアクタンスを一次側に割り当てます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: トランスを通る有効電力フローの初期条件（MW）。
  * `reactive_power_flow::Float64`: トランスを通る無効電力フローの初期条件（MVAR）。
  * `arc::Arc`: バスから別のバスへのこのトランスを定義する[`Arc`](@ref)。
  * `r::Float64`: puでの抵抗（[`SYSTEM_BASE`](@ref per_unit））、検証範囲: `(0, 4)`。
  * `x::Float64`: puでのリアクタンス（[`SYSTEM_BASE`](@ref per_unit））、検証範囲: `(-2, 4)`。
  * `primary_shunt::Float64`:、検証範囲: `(0, 2)`。
  * `tap::Float64`: 電圧制御のための正規化されたタップチェンジャーの位置で、0から2の間で変動し、1が定格電圧の中心にあります。検証範囲: `(0, 2)`。
  * `α::Float64`: `from`バスと`to`バス間の位相シフトの初期条件（ラジアン）、検証範囲: `(-1.571, 1.571)`。
  * `rating::Union{Nothing, Float64}`: 熱定格（MVA）。トランスを通るフローは-`rating`と`rating`の間でなければなりません。トランスを`System`に接続する前に定義する場合、`rating`は接続される`System`の基準電力を使用してpu（[`SYSTEM_BASE`](@ref per_unit））でなければなりません。検証範囲: `(0, nothing)`。
  * `phase_angle_limits::MinMax`: （デフォルト: `(min=-1.571, max=1.571)`）最小および最大位相角制限（ラジアン）、検証範囲: `(-1.571, 1.571)`。
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
