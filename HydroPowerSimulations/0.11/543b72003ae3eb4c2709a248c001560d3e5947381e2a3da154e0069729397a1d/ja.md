下流（下）貯水池の貯水レベルを追跡する制約を作成するための構造体

詳細については、[HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
e_{t}^\text{dn} = e_{t-1}^\text{dn} + \left (p_t^\text{hy,out} + s_t - \frac{p_t^\text{hy,in}}{\eta^\text{pump}} \right) \Delta T - \text{OutflowTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
