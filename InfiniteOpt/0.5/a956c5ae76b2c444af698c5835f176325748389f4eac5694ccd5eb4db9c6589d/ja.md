```
start_value_functionc(vref::GeneralVariableRef)
```

一般変数参照のための `start_value_function` を定義します。これは、基礎となる `DispatchVariableRef` に対して `start_value_function` が定義されていることに依存します。そうでない場合、`ArgumentError` がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
