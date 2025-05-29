```
JuMP.set_name(vref::GeneralVariableRef, name::String)::Nothing
```

`JuMP.set_name`を拡張して、`vref`の名前を設定します。これは、基盤となる`DispatchVariableRef`に対して`JuMP.set_name`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。
