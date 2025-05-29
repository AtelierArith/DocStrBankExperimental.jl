```
mutable struct TwoTerminalVSCDCLine <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    rectifier_tap_limits::MinMax
    rectifier_xrc::Float64
    rectifier_firing_angle::MinMax
    inverter_tap_limits::MinMax
    inverter_xrc::Float64
    inverter_extinction_angle::MinMax
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

電圧源コンバータ（VSC）-HVDC送電線。

フェデリコ・ミラノによる["電力システムのモデリングとスクリプティング"](https://link.springer.com/book/10.1007/978-3-642-13669-6)の第18章、397ページに実装されています。このモデルは動的シミュレーションに適しています。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: 線上のアクティブパワーフローの初期条件（MW）。
  * `arc::Arc`: バスから別のバスへのこの線を定義する[`Arc`](@ref)。
  * `rectifier_tap_limits::MinMax`: プライマリ側とセカンダリ側の電圧の比率としての最小および最大整流器タップ制限。
  * `rectifier_xrc::Float64`: 整流器のコミュテーションリアクタンス（p.u.）（[`DEVICE_BASE`](@ref per_unit)）。
  * `rectifier_firing_angle::MinMax`: 最小および最大整流器点火角（α）（ラジアン）。
  * `inverter_tap_limits::MinMax`: プライマリ側とセカンダリ側の電圧の比率としての最小および最大インバータタップ制限。
  * `inverter_xrc::Float64`: インバータのコミュテーションリアクタンス（p.u.）（[`DEVICE_BASE`](@ref per_unit)）。
  * `inverter_extinction_angle::MinMax`: 最小および最大インバータ消失角（γ）（ラジアン）。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)（例：緯度と経度）。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
