```
mutable struct TModelHVDCLine <: DCBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    r::Float64
    l::Float64
    c::Float64
    active_power_limits_from::MinMax
    active_power_limits_to::MinMax
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

高電圧DC送電線は、DC送電ネットワークのモデル化に使用されます。

このラインは、両端にある[`DCBus`](@ref)に接続されている必要があります。これは、ラインインピーダンスのTモデルを使用します。これは、マルチターミナルDCネットワークの運用シミュレーションに適しています。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: ライン上のアクティブパワーフローの初期条件（MW）。
  * `arc::Arc`: バスから別のバスへのこのラインを定義する[`Arc`](@ref)。
  * `r::Float64`: ショントキャパシタンスの両側で均等に分割されたp.u.での総直列抵抗（[`SYSTEM_BASE`](@ref per_unit)）。
  * `l::Float64`: ショントキャパシタンスの両側で均等に分割されたp.u.での総直列インダクタンス（[`SYSTEM_BASE`](@ref per_unit)）。
  * `c::Float64`: p.u.でのショントキャパシタンス（[`SYSTEM_BASE`](@ref per_unit)）。
  * `active_power_limits_from::MinMax`: FROMノードへの最小および最大アクティブパワーフロー（MW）。
  * `active_power_limits_to::MinMax`: TOノードへの最小および最大アクティブパワーフロー（MW）。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
