```
JuMP.is_fixed(vref::LogicalVariableRef)::Bool
```

`vref`が固定変数であれば`true`を返します。`true`の場合、固定値はfix_valueで照会できます。
