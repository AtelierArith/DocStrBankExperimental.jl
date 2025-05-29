```
JuMP.is_integer(vref::GeneralVariableRef)
```

一般変数参照に対する `JuMP.is_integer` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.is_integer` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
