ThermalMultiStartユニットの起動に関する制約を作成するための構造体。詳細については、[ThermalGen Formulations](@ref ThermalGen-Formulations)のThermalMultiStartUnitCommitmentを確認してください。

指定された制約は次のように定式化されています：

$$
\max\{P^\text{th,max} - P^\text{th,shdown}, 0\} \cdot w_1^\text{th} \le u^\text{th,init} (P^\text{th,max} - P^\text{th,min}) - P^\text{th,init}
$$
