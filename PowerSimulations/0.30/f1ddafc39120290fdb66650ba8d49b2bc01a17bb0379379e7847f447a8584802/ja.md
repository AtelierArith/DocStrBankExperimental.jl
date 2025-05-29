HVDC二端子ブランチを通るフロー制限を設定するための制約を作成する構造体。

詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
R^\text{min} \le f_t \le R^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
