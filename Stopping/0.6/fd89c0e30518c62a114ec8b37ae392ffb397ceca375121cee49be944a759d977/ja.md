タイプ: `GenericStopping`

メソッド: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`

最適性条件に関してインスタンスを解決するための一般的な停止です。最適性はスコアを計算し、それをゼロにテストすることによって決定されます。

追跡されるデータには以下が含まれます:

  * `pb`         : 問題
  * `current_state` : 問題に関連する情報、`GenericState`を参照。
  * (オプション) `meta` : 停止基準に関連するメタデータ、`StoppingMeta`を参照。
  * (オプション) `main_stp` : サブ問題の停止を考慮する場合のメインループの停止。                      サブ問題でない場合は、`VoidStopping`。
  * (オプション) `listofstates` : 状態の履歴を保存するために設計された`ListofStates`。
  * (オプション) `stopping_user_struct` : ユーザーによって設計された構造を含む。

コンストラクタ: 

  * `GenericStopping(pb, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    デフォルトコンストラクタ。
  * `GenericStopping(pb, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    `kwargs`を`stop_remote`に渡すもの。
  * `GenericStopping(pb, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    `kwargs`を`meta`に渡すもの。
  * `GenericStopping(pb, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    `kwargs`を`meta`に渡すもの。
  * `GenericStopping(pb, x; n_listofstates=, kwargs...)`    xを使用してデフォルトの状態を設定し、`n_listofstates>0`の場合に状態のリストを初期化するもの。

注意: メタデータはユーザーによって提供されるか、`kwargs`を介して停止コンストラクタで作成されます。特定の`StoppingMeta`が与えられ、`kwargs`が提供される場合、`kwargs`が優先されます。

例:  `GenericStopping(pb, GenericState(ones(2)), rtol = 1e-1)`

最適性条件に加えて、古典的な緊急終了を考慮します:

  * ドメインエラー        (例えば: xにNaN)
  * 無限大の問題       (未実装)
  * 無限大のx         (xが大きすぎる)
  * 疲れた問題       (時間制限に達した)
  * リソース枯渇 (未実装)
  * 停滞した問題     (未実装)
  * 繰り返し制限     (最大繰り返し数 (すなわち停止数) に達した)
  * main_pb制限       (メイン問題の疲れまたはリソースが枯渇)

デフォルトの状態を持つ停止を作成する追加のデフォルトコンストラクタがあります。

`GenericStopping(:: Any, :: Union{Number, AbstractVector}; kwargs...)`

注意: キーワード引数は古典的なコンストラクタに転送されます。

例:  `GenericStopping(pb, x0, rtol = 1e-1)`
