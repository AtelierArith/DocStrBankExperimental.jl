```
JuMP.has_lower_bound(vref::GeneralVariableRef)
```

一般的な変数参照に対する `JuMP.has_lower_bound` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.has_lower_bound` が定義されていることに依存します。そうでない場合、`ArgumentError` がスローされます。詳細については、基礎となるドキュメントを参照してください。
