ロスのあるHVDC二端子ライン全体の電力バランスを設定する制約を作成するための構造体。

詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\begin{align*}
& f_t^\text{to-from} - f_t^\text{from-to} \le L_1 \cdot f_t^\text{to-from} - L_0,\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{from-to} - f_t^\text{to-from} \ge L_1 \cdot f_t^\text{from-to} + L_0,\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{from-to} - f_t^\text{to-from} \ge - M^\text{big} (1 - u^\text{dir}_t),\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{to-from} - f_t^\text{from-to} \ge - M^\text{big} u^\text{dir}_t,\quad \forall t \in \{1,\dots, T\} \\
\end{align*}
$$
