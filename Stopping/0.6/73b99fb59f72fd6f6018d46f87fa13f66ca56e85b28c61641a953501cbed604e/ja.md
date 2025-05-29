タイプ: NLPStopping

メソッド: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`, `KKT`, `unconstrained_check`, `optim_check_bounded`

`GenericStopping`の特化。`NLPModels`を使用した非線形最適化モデルのための停止構造 ( https://github.com/JuliaSmoothOptimizers/NLPModels.jl )。

属性:

  * `pb`         : `AbstractNLPModel`。
  * `current_state`      : 問題に関連する情報、`GenericState`または`NLPAtX`を参照。
  * (opt) `meta` : 停止基準に関連するメタデータ、`StoppingMeta`を参照。
  * (opt) `main_stp` : サブ問題の停止を考慮する場合のメインループの停止。サブ問題でない場合は`VoidStopping`。
  * (opt) `listofstates` : 状態の履歴を保存するために設計されたListofStates。
  * (opt) `stopping_user_struct` : ユーザーによって設計された任意の構造を含む。

コンストラクタ:

  * `NLPStopping(pb::AbstractNLPModel, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    デフォルトのコンストラクタ。
  * `NLPStopping(pb::AbstractNLPModel, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    `kwargs`を`stop_remote`に渡すもの。
  * `GenericStopping(pb::AbstractNLPModel, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    `kwargs`を`meta`に渡すもの。
  * `GenericStopping(pb::AbstractNLPModel; n_listofstates=, kwargs...)`    `pb.meta.x0`を使用してデフォルトの状態`NLPAtX`を設定し、`n_listofstates>0`の場合に状態のリストを初期化するもの。最適性関数は`KKT`関数であり、`optimality_check`が`kwargs`に含まれていない限り。

ノート:

  * `NLPAtX`状態用に設計されています。コンストラクタは、状態が必要なエントリを持っていることを確認します。
