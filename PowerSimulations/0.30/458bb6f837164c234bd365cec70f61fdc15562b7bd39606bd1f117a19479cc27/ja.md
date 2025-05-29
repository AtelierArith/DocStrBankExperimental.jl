HVDC二端子ブランチを通じて流れの制限を設定するための制約を作成する構造体。

詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
R^\text{from,min} \le f_t^\text{from-to}  \le R^\text{from,max}, \forall t \in \{1,\dots, T\}
$$
