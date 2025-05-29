```
JuMP.name(vref::GeneralVariableRef)::String
```

`JuMP.name`を拡張して、`vref`の名前を返すようにします。これは、基盤となる`DispatchVariableRef`に対して`JuMP.name`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。
