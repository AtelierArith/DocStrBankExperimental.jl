```
JuMP.unset_integer(vref::GeneralVariableRef)
```

一般変数参照のための `JuMP.unset_integer` を定義します。これは、基盤となる `DispatchVariableRef` に対して `JuMP.unset_integer` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基盤となるドキュメント文字列を参照してください。
