```
JuMP.set_upper_bound(vref::GeneralVariableRef, value::Real)::Nothing
```

一般変数参照のための `JuMP.set_upper_bound` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.set_upper_bound` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
