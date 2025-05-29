アクティブパワーリザーブの参加割り当て制限を作成するための制約を定義する構造体。詳細については[Service Formulations](@ref service_formulations)を参照してください。

制約は次のとおりです：

$$
r_{d,t} \le \text{Req} \cdot \text{PF} ,\quad \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\} \quad \text{(for a ConstantReserve)} \\
r_{d,t} \le \text{RequirementTimeSeriesParameter}_{t} \cdot \text{PF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for a VariableReserve)}
$$
