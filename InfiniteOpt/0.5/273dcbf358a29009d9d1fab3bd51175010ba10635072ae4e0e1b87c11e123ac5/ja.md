```
JuMP.is_binary(vref::GeneralVariableRef)
```

`JuMP.is_binary`を一般変数参照のために定義します。これは、基礎となる`DispatchVariableRef`に対して`JuMP.is_binary`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については、基礎となるドキュメントを参照してください。
