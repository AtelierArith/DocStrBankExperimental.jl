```
set_start_value_function(vref::GeneralVariableRef, start::Union{Real, Function})::Nothing
```

`vref`の開始値関数を設定します。これは、基盤となる`DispatchVariableRef`に対して`set_start_value_function`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。
