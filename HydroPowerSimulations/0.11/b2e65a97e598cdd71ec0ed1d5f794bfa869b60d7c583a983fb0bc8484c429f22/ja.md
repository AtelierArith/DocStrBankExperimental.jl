上流（up）貯水池の水位を追跡する制約を作成するための構造体

詳細については、[HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
e_{t}^\text{up} = e_{t-1}^\text{up} + \left (p_t^\text{hy,in} - \frac{p_t^\text{hy,out} + s_t}{\eta^\text{pump}} \right) \Delta T + \text{InflowTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
