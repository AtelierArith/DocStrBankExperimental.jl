```
JuMP.start_value(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.start_value` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.start_value` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
