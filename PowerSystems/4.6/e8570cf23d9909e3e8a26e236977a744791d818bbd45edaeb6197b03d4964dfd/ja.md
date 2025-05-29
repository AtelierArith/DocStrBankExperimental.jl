```
mutable struct ThermalStandard <: ThermalGen
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    operation_cost::Union{ThermalGenerationCost, MarketBidCost}
    base_power::Float64
    time_limits::Union{Nothing, UpDown}
    must_run::Bool
    prime_mover_type::PrimeMovers
    fuel::ThermalFuels
    services::Vector{Service}
    time_at_status::Float64
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

化石燃料や原子力発電所などの熱発電機。

これは、最小稼働時間、最小停止時間、およびランプ制限を含むオプションを持つ標準的な表現です。より詳細な表現については、起動およびシャットダウンプロセス（ホットスタートを含む）を参照してください[`ThermalMultiStart`](@ref)

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます
  * `status::Bool`: シミュレーション開始時の初期コミットメント条件（`true` = オンまたは`false` = オフ）
  * `bus::ACBus`: このコンポーネントが接続されているバス
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これは使用されるソルバーによって初期の出発点として使用される場合とされない場合があります。検証範囲：`active_power_limits`
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）、検証範囲：`reactive_power_limits`
  * `rating::Float64`: ユニットの最大出力パワー定格（MVA）、検証範囲：`(0, nothing)`
  * `active_power_limits::MinMax`: 最小および最大の安定したアクティブパワーレベル（MW）、検証範囲：`(0, nothing)`
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大のリアクティブパワー制限。該当しない場合は`Nothing`に設定
  * `ramp_limits::Union{Nothing, UpDown}`: MW/分のランプアップおよびランプダウン制限、検証範囲：`(0, nothing)`
  * `operation_cost::Union{ThermalGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref) の発電コスト
  * `base_power::Float64`: [単位化](@ref per_unit) のためのユニットのベースパワー（MVA）、検証範囲：`(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: （デフォルト：`nothing`）最小稼働時間および最小停止時間制限（時間単位）、検証範囲：`(0, nothing)`
  * `must_run::Bool`: （デフォルト：`false`）ユニットが必ず稼働する場合は`true`に設定
  * `prime_mover_type::PrimeMovers`: （デフォルト：`PrimeMovers.OT`）EIA 923に従ったプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています
  * `fuel::ThermalFuels`: （デフォルト：`ThermalFuels.OTHER`）EIA 923に従ったプライムムーバー燃料。オプションは[こちら](@ref tf_list)にリストされています
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス
  * `time_at_status::Float64`: （デフォルト：`INFINITE_TIME`）ジェネレーターがオンまたはオフであった時間（例：`Hours(6)`）、`status`によって示される
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）対応する動的注入デバイス
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
