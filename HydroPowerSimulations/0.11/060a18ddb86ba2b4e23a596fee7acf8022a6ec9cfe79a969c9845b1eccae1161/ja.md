貯水池の定式化に対する予算を制限する制約を作成するための構造体。

詳細については、[HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\sum_{t=1}^T p^\text{hy}_t \le \sum_{t=1}^T \text{EnergyBudgetTimeSeriesParameter}_t,
$$
