`init_model_discrete(model::AbstractEpiModel, g::AbstractGraph, rng::AbstractRNG, state_base::Symbol)`

シミュレーション内のすべてのノードを同じ基本状態に初期化し、アクティブな感染はありません。

すべてのノードは`state_base`に設定され、遅延、状態、および感染履歴のデフォルト値が割り当てられます。`SimData`構造体を返します。
