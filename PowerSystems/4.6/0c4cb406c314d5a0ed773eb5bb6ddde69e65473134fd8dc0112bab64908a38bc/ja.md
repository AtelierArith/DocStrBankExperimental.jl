```
mutable struct ThermalMultiStart <: ThermalGen
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    fuel::ThermalFuels
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    power_trajectory::Union{Nothing, StartUpShutDown}
    time_limits::Union{Nothing, UpDown}
    start_time_limits::Union{Nothing, StartUpStages}
    start_types::Int
    operation_cost::Union{ThermalGenerationCost, MarketBidCost}
    base_power::Float64
    services::Vector{Service}
    time_at_status::Float64
    must_run::Bool
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

熱源発電機、例えば化石燃料や原子力発電機は、*熱い*、*温かい*、または*冷たい*状態から再起動することができます。

`ThermalMultiStart`は、最後のシャットダウンから経過した時間に基づく起動プロセスの詳細な表現と、詳細なシャットダウンプロセスを持っています。このモデルは、["Tight and Compact MILP Formulation for the Thermal Unit Commitment Problem."](https://doi.org/10.1109/TPWRS.2013.2251373)に基づいています。起動およびシャットダウンプロセスの簡略化された表現については、[`ThermalStandard`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `status::Bool`: シミュレーション開始時の初期コミットメント条件（`true` = オンまたは`false` = オフ）。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `active_power::Float64`: ユニットの初期アクティブパワー設定値（MW）。電力フローの場合、これはシステムの定常状態の動作点です。生産コストモデリングの場合、これは使用されるソルバーに応じて初期の出発点として使用される場合と使用されない場合があります。検証範囲：`active_power_limits`
  * `reactive_power::Float64`: ユニットの初期リアクティブパワー設定値（MVAR）、検証範囲：`reactive_power_limits`
  * `rating::Float64`: ユニットの最大出力パワー定格（MVA）、検証範囲：`(0, nothing)`
  * `prime_mover_type::PrimeMovers`: EIA 923に基づくプライムムーバー技術。オプションは[こちら](@ref pm_list)にリストされています。
  * `fuel::ThermalFuels`: EIA 923に基づくプライムムーバー燃料。オプションは[こちら](@ref tf_list)にリストされています。
  * `active_power_limits::MinMax`: 最小および最大の安定アクティブパワーレベル（MW）。
  * `reactive_power_limits::Union{Nothing, MinMax}`: 最小および最大のリアクティブパワー制限。該当しない場合は`Nothing`に設定します。
  * `ramp_limits::Union{Nothing, UpDown}`:, 検証範囲：`(0, nothing)`
  * `power_trajectory::Union{Nothing, StartUpShutDown}`: ユニットが起動およびシャットダウンのランププロセス中に取るパワー軌道、検証範囲：`(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: 最小のアップおよびダウン時間制限（時間単位）、検証範囲：`(0, nothing)`
  * `start_time_limits::Union{Nothing, StartUpStages}`: タービン温度に基づく起動の時間制限（時間単位）。
  * `start_types::Int`: タービン温度に基づく起動の数。`1` = *熱い*、`2` = *温かい*、`3` = *冷たい*、検証範囲：`(1, 3)`
  * `operation_cost::Union{ThermalGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref)の発電。
  * `base_power::Float64`: [単位化](@ref per_unit)のためのユニットの基準パワー（MVA）、検証範囲：`(0, nothing)`
  * `services::Vector{Service}`: (デフォルト：`Device[]`) このデバイスが貢献するサービス。
  * `time_at_status::Float64`: (デフォルト：`INFINITE_TIME`) ジェネレーターがオンまたはオフであった時間（例：`Hours(6)`）、`status`によって示されます。
  * `must_run::Bool`: (デフォルト：`false`) ユニットが必ず稼働する場合は`true`に設定します。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (デフォルト：`nothing`) 対応する動的注入デバイス。
  * `ext::Dict{String, Any}`: (デフォルト：`Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)。例えば、緯度や経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照。
