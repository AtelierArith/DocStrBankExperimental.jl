```
used_by_semi_infinite_variable(vref::GeneralVariableRef)::Bool
```

`used_by_semi_infinite_variable`を一般的な変数参照のために定義します。これは、基礎となる`DispatchVariableRef`に対して`used_by_semi_infinite_variable`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
