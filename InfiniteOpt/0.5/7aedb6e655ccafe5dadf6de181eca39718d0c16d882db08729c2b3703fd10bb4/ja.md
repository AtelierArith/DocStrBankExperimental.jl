```
used_by_derivative(vref::GeneralVariableRef)::Bool
```

`used_by_derivative`を一般変数参照のために定義します。これは、基礎となる`DispatchVariableRef`に対して`used_by_derivative`が定義されていることに依存します。そうでない場合、`ArgumentError`がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
