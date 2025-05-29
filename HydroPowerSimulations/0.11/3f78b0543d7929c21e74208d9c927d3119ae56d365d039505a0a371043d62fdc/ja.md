貯水池の定式化のターゲットを設定する制約を作成するための構造体。

詳細については、[HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
e_t + e^\text{shortage} + e^\text{surplus} = \text{EnergyTargetTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
