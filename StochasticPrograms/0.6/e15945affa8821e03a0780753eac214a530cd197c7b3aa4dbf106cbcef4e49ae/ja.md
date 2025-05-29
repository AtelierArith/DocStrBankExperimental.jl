```
normalized_coefficient(sp_cref::SPConstraintRef, dvar::DecisionVariable, scenario_index::Integer)
```

`scenario_index`の決定制約`sp_cref`における`dvar`に関連付けられた係数を返します。これは、JuMPが制約を標準形に正規化した後のものです。
