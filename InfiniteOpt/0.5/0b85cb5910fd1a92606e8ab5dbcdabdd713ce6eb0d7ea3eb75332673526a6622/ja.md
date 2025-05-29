```
JuMP.set_value(vref::DispatchVariableRef, value::Real)::Nothing
```

`JuMP.set_value`を拡張して、`vref`の値を設定します。これは、基盤となる`DispatchVariableRef`に対して`JuMP.set_value`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。
