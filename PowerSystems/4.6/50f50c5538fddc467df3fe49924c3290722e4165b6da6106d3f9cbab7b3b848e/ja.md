```
mutable struct RenewableNonDispatch <: RenewableGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    power_factor::Float64
    base_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

非 dispatchable（すなわち、カーテイブルでないまたは必須の）再生可能発電機。

その出力はデフォルトでその [`max_active_power` 時系列](@ref ts_data) に等しい。使用例：屋根上太陽光などのメーター背後の分散型エネルギー資源の集約。カーテイブルまたは下方 dispatchable 発電については、[`RenewableDispatch`](@ref) を参照してください。

再生可能発電機には `max_active_power` パラメータはなく、代わりに [`get_max_active_power()`](@ref get_max_active_power(d::T) where {T <: RenewableGen}) を呼び出す際に計算されます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これは使用されるソルバーに応じて初期の出発点として使用される場合と使用されない場合があります。
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）、一部の生産コストモデリングシミュレーションで使用されます。負荷フローでリアクティブパワーを設定するには、`power_factor` を使用します。
  * `rating::Float64`: ユニットの最大出力電力定格（MVA）、検証範囲: `(0, nothing)`
  * `prime_mover_type::PrimeMovers`: EIA 923 に従ったプライムムーバー技術。オプションは [こちら](@ref pm_list) にリストされています。
  * `power_factor::Float64`: パワーファクター [0, 1] 設定値、一部の生産コストモデリングおよびユニットが [`PQ`](@ref acbustypes_list) バスに接続されている場合の負荷フローで使用されます。検証範囲: `(0, 1)`
  * `base_power::Float64`: [単位化](@ref per_unit) のためのユニットの基準電力（MVA）、検証範囲: `(0, nothing)`
  * `services::Vector{Service}`: (デフォルト: `Device[]`) このデバイスが貢献するサービス。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (デフォルト: `nothing`) 対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するためのユーザー用の [*ext*ra 辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照。
