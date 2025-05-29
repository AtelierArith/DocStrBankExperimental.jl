ブランチを通るACフロー制限を設定するための制約を作成する構造体。

詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は次のように定式化されます：

$$
\begin{align*}
&  f_t - f_t^\text{sl,up} \le R^\text{max},\quad \forall t \in \{1,\dots, T\} \\
&  f_t + f_t^\text{sl,lo} \ge -R^\text{max},\quad \forall t \in \{1,\dots, T\}
\end{align*}
$$
