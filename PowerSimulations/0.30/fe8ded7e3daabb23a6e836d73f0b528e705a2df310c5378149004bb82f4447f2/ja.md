半連続フィードフォワード制限のための制約を作成する構造体。

詳細については、[Feedforward Formulations](@ref ff_formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\begin{align*}
&  \text{ActivePowerRangeExpressionUB}_t := p_t^\text{th} - \text{on}_t^\text{th}P^\text{th,max} \le 0, \quad  \forall t\in \{1, \dots, T\}  \\
&  \text{ActivePowerRangeExpressionLB}_t := p_t^\text{th} - \text{on}_t^\text{th}P^\text{th,min} \ge 0, \quad  \forall t\in \{1, \dots, T\}
\end{align*}
$$
