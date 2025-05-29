```
JuMP.IntegerRef(vref::GeneralVariableRef)
```

`JuMP.IntegerRef`を一般変数参照のために定義します。これは、基礎となる`DispatchVariableRef`に対して`JuMP.IntegerRef`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
