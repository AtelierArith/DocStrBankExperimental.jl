```
mutable struct Source <: StaticInjection
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    R_th::Float64
    X_th::Float64
    internal_voltage::Float64
    internal_angle::Float64
    base_power::Float64
    dynamic_injector::Union{Nothing, DynamicInjection}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

定常電圧出力を持つ無限バス。

ダイナミクスシミュレーションで、単一バス上の非常に大きな機械を表すために一般的に使用されます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期有効電力設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これはソルバーによって初期の出発点として使用される場合とされない場合があります。
  * `reactive_power::Float64`: ユニットの初期無効電力設定値（MVAR）。
  * `R_th::Float64`: ソースのテブナン抵抗、検証範囲: `(0, nothing)`。
  * `X_th::Float64`: ソースのテブナンリアクタンス、検証範囲: `(0, nothing)`。
  * `internal_voltage::Float64`: （デフォルト: `1.0`）内部電圧（pu）、検証範囲: `(0, nothing)`。
  * `internal_angle::Float64`: （デフォルト: `0.0`）内部角度。
  * `base_power::Float64`: （デフォルト: `100.0`）MVA単位の基準電力。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）対応する動的注入デバイス。
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
