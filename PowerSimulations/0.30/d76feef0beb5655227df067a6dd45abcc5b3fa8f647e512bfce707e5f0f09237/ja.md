指定された領域間で電力をバランスさせるための制約を作成する構造体。詳細については[Network Formulations](@ref network_formulations)を確認してください。

指定された制約は一般的に次のように定式化されます：

$$
\sum_{c \in \text{components}_a} p_t^c = 0, \quad \forall a\in \{1,\dots, A\}, t \in \{1, \dots, T\}
$$
