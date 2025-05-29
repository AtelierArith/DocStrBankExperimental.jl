```
JuMP.delete(model::InfiniteModel, vref::GeneralVariableRef)::Nothing
```

`JuMP.delete`を拡張して、`vref`とその依存関係を削除します。これは、基盤となる`DispatchVariableRef`に対して`JuMP.delete`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。
