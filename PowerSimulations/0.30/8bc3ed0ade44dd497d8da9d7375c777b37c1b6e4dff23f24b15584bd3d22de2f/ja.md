オン、スタート、およびストップ変数間のコミットメント制約を作成するための構造体。詳細については[ThermalGen Formulations](@ref ThermalGen-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
u_1^\text{th} = u^\text{th,init} + v_1^\text{th} - w_1^\text{th} \\
u_t^\text{th} = u_{t-1}^\text{th} + v_t^\text{th} - w_t^\text{th}, \quad \forall t \in \{2,\dots,T\} \\
v_t^\text{th} + w_t^\text{th} \le 1, \quad \forall t \in \{1,\dots,T\}
$$
