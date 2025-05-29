```
mutable struct TapTransformer <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    reactive_power_flow::Float64
    arc::Arc
    r::Float64
    x::Float64
    primary_shunt::Float64
    tap::Float64
    rating::Union{Nothing, Float64}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

タップチェンジャーを備えた2巻線変圧器。

このモデルは、インピーダンスが変圧器の高電圧側にあると仮定した等価回路を使用します。このモデルは、鉄損失と励磁サスペンションを一次側に割り当てます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: 変圧器を通る有効電力フローの初期条件（MW）。
  * `reactive_power_flow::Float64`: 変圧器を通る無効電力フローの初期条件（MVAR）。
  * `arc::Arc`: この変圧器をバスから別のバスへ定義する[`Arc`](@ref)。
  * `r::Float64`: p.u.での抵抗（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲：`(-2, 2)`。
  * `x::Float64`: p.u.でのリアクタンス（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲：`(-2, 4)`。
  * `primary_shunt::Float64`: p.u.でのシャントリアクタンス（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲：`(0, 2)`。
  * `tap::Float64`: 電圧制御のための正規化されたタップチェンジャー位置。0から2の間で変動し、1は公称電圧の中心に位置します。検証範囲：`(0, 2)`。
  * `rating::Union{Nothing, Float64}`: 熱定格（MVA）。変圧器を通るフローは-`rating`の間でなければなりません。変圧器を`System`に接続する前に定義する場合、`rating`は接続される`System`の基準電力を使用してpu（[`SYSTEM_BASE`](@ref per_unit)）でなければなりません。検証範囲：`(0, nothing)`。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
