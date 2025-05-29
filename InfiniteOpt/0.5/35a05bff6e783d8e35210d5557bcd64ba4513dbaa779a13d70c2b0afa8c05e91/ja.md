```
JuMP.lower_bound(vref::GeneralVariableRef)
```

一般変数参照に対する `JuMP.lower_bound` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.lower_bound` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
