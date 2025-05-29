指定された熱デバイスまたは予備サービスに関連付けられたRampConstraintを作成するための構造体。

熱ユニットについては、[Thermal Formulations](@ref ThermalGen-Formulations)で詳細情報を参照してください。制約は次のとおりです：

$$
-R^\text{th,dn} \le p_t^\text{th} - p_{t-1}^\text{th} \le R^\text{th,up}, \quad \forall  t\in \{1, \dots, T\}
$$

Ramp Reserveについては、[Service Formulations](@ref service_formulations)で詳細情報を参照してください。制約は次のとおりです：

$$
r_{d,t} \le R^\text{th,up} \cdot \text{TF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for ReserveUp)} \\
r_{d,t} \le R^\text{th,dn} \cdot \text{TF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for ReserveDown)}
$$
