入力 `x` から出力 `y` への線形マッピングの抽象的な表現で、形式は `YΦ = Px`, `y = QᵀΦ` です。サブタイプ U <: AdmittanceModel は以下を実装することが期待されています：

```
get_Y(am::U)
get_P(am::U)
get_Q(am::U)
get_ports(am::U)
partial_copy(am::U; Y, P, ports)
compatible(AbstractVector{U})
```
