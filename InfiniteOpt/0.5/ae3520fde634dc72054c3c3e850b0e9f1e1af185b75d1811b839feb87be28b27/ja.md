```
JuMP.set_integer(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.set_integer` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.set_integer` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基礎となるドキュメントを参照してください。
