```
infinite_variable_refc(vref::GeneralVariableRef)
```

一般的な変数参照のための `infinite_variable_ref` を定義します。これは、基礎となる `DispatchVariableRef` に対して `infinite_variable_ref` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
