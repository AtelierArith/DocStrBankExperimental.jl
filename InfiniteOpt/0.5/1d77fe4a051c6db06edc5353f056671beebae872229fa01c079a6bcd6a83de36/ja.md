```
JuMP.FixRef(vref::GeneralVariableRef)
```

一般的な変数参照のための `JuMP.FixRef` を定義します。これは、基盤となる `DispatchVariableRef` に対して `JuMP.FixRef` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基盤となるドキュメント文字列を参照してください。
