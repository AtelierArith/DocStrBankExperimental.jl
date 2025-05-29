```
JuMP.has_upper_bound(vref::GeneralVariableRef)
```

一般的な変数参照に対して `JuMP.has_upper_bound` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.has_upper_bound` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
