```
parameter_valuesc(vref::GeneralVariableRef)
```

一般変数参照のための`parameter_values`を定義します。これは、基礎となる`DispatchVariableRef`に対して`parameter_values`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については、基礎となるドキュメント文字列を参照してください。
