```
JuMP.fix_value(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.fix_value` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.fix_value` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
