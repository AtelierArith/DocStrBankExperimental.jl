```
JuMP.set_start_value(vref::GeneralVariableRef, value::Real)::Nothing
```

一般変数参照のための `JuMP.set_start_value` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.set_start_value` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
