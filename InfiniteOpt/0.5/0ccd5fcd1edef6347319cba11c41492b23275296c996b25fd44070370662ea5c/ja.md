```
is_used(vref::GeneralVariableRef)::Bool
```

一般的な変数参照のために `is_used` を定義します。これは、基礎となる `DispatchVariableRef` に対して `is_used` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
