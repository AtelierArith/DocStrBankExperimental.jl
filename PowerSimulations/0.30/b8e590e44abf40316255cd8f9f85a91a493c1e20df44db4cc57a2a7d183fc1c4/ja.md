非回転予備がオフにした熱ユニットから供給されることを保証するための制約を作成する構造体。

詳細については、非回転予備に関する[サービスの定式化](@ref service_formulations)を確認してください。

制約は次のとおりです：

$$
r_{d,t} \le (1 - u_{d,t}^\text{th}) \cdot R^\text{limit}_d, \quad \forall d \in \mathcal{D}_s, \forall t \in \{1,\dots, T\}
$$
