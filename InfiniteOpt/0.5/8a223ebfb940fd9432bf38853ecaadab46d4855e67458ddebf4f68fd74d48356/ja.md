```
JuMP.unset_binary(vref::GeneralVariableRef)
```

一般変数参照に対して `JuMP.unset_binary` を定義します。これは、基盤となる `DispatchVariableRef` に対して `JuMP.unset_binary` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基盤となるドキュメントを参照してください。
