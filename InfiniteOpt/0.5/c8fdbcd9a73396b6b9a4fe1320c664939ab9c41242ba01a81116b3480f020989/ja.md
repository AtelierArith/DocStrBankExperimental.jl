```
JuMP.LowerBoundRef(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.LowerBoundRef` を定義します。これは、基になる `DispatchVariableRef` に対して `JuMP.LowerBoundRef` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基になるドキュメントを参照してください。
