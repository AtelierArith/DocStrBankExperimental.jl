```
JuMP.normalized_coefficient(cref::InfOptConstraintRef,
                            variable::GeneralVariableRef)::Float64
```

`constraint`における`variable`に関連付けられた係数を返します。これは、JuMPが制約を標準形に正規化した後のものです。
