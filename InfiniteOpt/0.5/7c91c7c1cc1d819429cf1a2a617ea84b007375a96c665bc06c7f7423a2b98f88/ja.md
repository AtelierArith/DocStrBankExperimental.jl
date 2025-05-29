```
JuMP.unfix(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.unfix` を定義します。これは、基盤となる `DispatchVariableRef` に対して `JuMP.unfix` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基盤となるドキュメントを参照してください。
