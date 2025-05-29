```
mutable struct TwoTerminalHVDCLine <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    active_power_limits_from::MinMax
    active_power_limits_to::MinMax
    reactive_power_limits_from::MinMax
    reactive_power_limits_to::MinMax
    loss::Union{LinearCurve, PiecewiseIncrementalCurve}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

高電圧直流（HVDC）ラインで、両端にそれぞれ[`ACBus`](@ref)に接続される必要があります。

このモデルは、損失が電力フローに比例する線形化されたDC電力フロー近似を用いた運用シミュレーションに適しています。DCネットワークのモデル化については、[`TModelHVDCLine`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: ライン上のアクティブ電力フローの初期条件（MW）。
  * `arc::Arc`: バスから別のバスへのこのラインを定義する[`Arc`](@ref)。
  * `active_power_limits_from::MinMax`: FROMノードへの最小および最大アクティブ電力フロー（MW）。
  * `active_power_limits_to::MinMax`: TOノードへの最小および最大アクティブ電力フロー（MW）。
  * `reactive_power_limits_from::MinMax`: FROMノードへの最小および最大リアクティブ電力制限（MVAR）。
  * `reactive_power_limits_to::MinMax`: TOノードへの最小および最大リアクティブ電力制限（MVAR）。
  * `loss::Union{LinearCurve, PiecewiseIncrementalCurve}`: （デフォルト：`LinearCurve(0.0)`）損失モデル係数。定数損失（MW）と比例損失率（MWの流れあたりの損失MW）を持つ線形モデルを受け入れます。また、異なるセグメントに対して異なる比例損失を指定するためのNセグメントを持つPiecewise損失も受け入れます。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)。例えば、緯度や経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
