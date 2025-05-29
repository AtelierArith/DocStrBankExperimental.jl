タイプ: LAStopping

メソッド: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`, `linear_system_check`, `normal_equation_check`

GenericStoppingの特殊化。線形代数の解法のための停止構造、次のいずれかを解くために

$$
Ax = b
$$

または

$$
min\_{x} \tfrac{1}{2}\|Ax - b\|^2
$$

属性:

  * `pb`         : 例えば、`LLSModel`（線形最小二乗問題用に設計された、https://github.com/JuliaSmoothOptimizers/LLSModels.jl を参照）または`LinearSystem`を使用する問題。
  * `current_state`      : 問題に関連する情報、`GenericState`を参照。
  * (オプション) `meta` : 停止基準に関連するメタデータ、`StoppingMeta`を参照。
  * (オプション) `main_stp` : サブ問題の停止を考慮する場合のメインループの停止。サブ問題でない場合は`VoidStopping`。
  * (オプション) `listofstates` : 状態の履歴を保存するために設計されたListofStates。
  * (オプション) `stopping_user_struct` : ユーザーによって設計された構造を含む。

コンストラクタ:

  * `LAStopping(pb, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false)`    デフォルトのコンストラクタ。
  * `LAStopping(pb, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false, kwargs...)`    `kwargs`を`stop_remote`に渡すもの。
  * `LAStopping(pb, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false, kwargs...)`    `kwargs`を`meta`に渡すもの。
  * `LAStopping(:: Union{AbstractLinearOperator, AbstractMatrix}, :: AbstractVector; sparse::Bool = true, n_listofstates::Int = 0, kwargs...)`    デフォルトの問題（`sparse ? LLSModel(A, b) : LinearSystem(A, b)`）を設定し、xを使用してデフォルトの`GenericState`を作成し、`n_listofstates>0`の場合に状態のリストを初期化するもの。
  * `LAStopping(:: Union{AbstractLinearOperator, AbstractMatrix}, :: AbstractVector, :: AbstractState; sparse::Bool = true, kwargs...)`    デフォルトの問題（`sparse ? LLSModel(A, b) : LinearSystem(A, b)`）を設定するもの。

注意:

  * 特定の状態はターゲットにされていない
  * 状態は必ずしもevalsを追跡するわけではない
  * evalsは`pb.A`がLinearOperatorである場合のみチェックされる
  * `zero_start`は0が初期推測である場合にtrue（自動的にはチェックされない）
  * `LLSModel`カウンターは`NLSCounters`に従う（`init_max_counters_NLS`を参照）
  * デフォルトでは、`meta.max_cntrs`はNLSCountersで初期化される

他に`GenericStopping`、`NLPStopping`、`linear_system_check`、`normal_equation_check`を参照。
