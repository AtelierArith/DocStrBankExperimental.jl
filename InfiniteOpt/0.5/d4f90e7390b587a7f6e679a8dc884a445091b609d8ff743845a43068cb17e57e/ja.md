```
JuMP.set_binary(vref::GeneralVariableRef)
```

一般的な変数参照に対して `JuMP.set_binary` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.set_binary` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
