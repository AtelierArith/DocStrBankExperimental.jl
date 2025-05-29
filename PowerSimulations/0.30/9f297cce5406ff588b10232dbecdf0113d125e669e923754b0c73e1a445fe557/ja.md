アクティブパワーリザーブ要件を満たすための制約を作成するための構造体。詳細については[Service Formulations](@ref service_formulations)を確認してください。

制約は次のとおりです：

$$
\sum_{d\in\mathcal{D}_s} r_{d,t} + r_t^\text{sl} \ge \text{Req},\quad \forall t\in \{1,\dots, T\} \quad \text{(定常リザーブの場合)} \\
\sum_{d\in\mathcal{D}_s} r_{d,t} + r_t^\text{sl} \ge \text{RequirementTimeSeriesParameter}_{t},\quad \forall t\in \{1,\dots, T\} \quad \text{(可変リザーブの場合)}
$$
