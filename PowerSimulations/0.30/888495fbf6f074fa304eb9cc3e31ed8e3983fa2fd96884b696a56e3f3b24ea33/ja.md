PhaseShiftingTransformerを通じて角度制限を設定するための制約を作成する構造体。

詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\Theta^\text{min} \le \theta^\text{shift}_t \le \Theta^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
