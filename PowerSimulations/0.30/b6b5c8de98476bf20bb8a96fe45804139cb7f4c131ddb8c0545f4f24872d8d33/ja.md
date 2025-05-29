上限フィードフォワード制限のための制約を作成する構造体。

詳細については、[Feedforward Formulations](@ref ff_formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\begin{align*}
&  \text{AffectedVariable}_t - p_t^\text{ff,ubsl} \le \text{SourceVariableParameter}_t, \quad \forall t \in \{1,\dots, T\}
\end{align*}
$$
