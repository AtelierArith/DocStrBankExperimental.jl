`set_state_nodes(model::AbstractEpiModel, data::SimData, rng::AbstractRNG, nodes::Vector{I}, state::Symbol, active::Bool; tset::Integer=0) where I <: Integer`

指定されたノードに状態を割り当て、必要に応じてそれらをアクティブにします。

`nodes`内のすべてのノードの状態を`state`に更新します。状態がアクティブとしてマークされているか、`active`がtrueの場合、モデルと乱数生成器を使用して感染メタデータと遷移遅延を更新します。

### オプション引数

  * `tset`: 感染および遷移追跡のために割り当てる時間（デフォルト: 0）。
