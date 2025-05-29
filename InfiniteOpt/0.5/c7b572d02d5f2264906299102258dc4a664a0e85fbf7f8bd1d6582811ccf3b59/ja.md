```
JuMP.is_fixed(vref::GeneralVariableRef)
```

一般変数参照に対する `JuMP.is_fixed` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.is_fixed` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基礎となるドキュメントを参照してください。
