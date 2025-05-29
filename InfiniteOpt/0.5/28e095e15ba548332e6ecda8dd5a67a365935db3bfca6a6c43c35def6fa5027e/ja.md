```
JuMP.BinaryRef(vref::GeneralVariableRef)
```

`JuMP.BinaryRef`を一般的な変数参照のために定義します。これは、基盤となる`DispatchVariableRef`に対して`JuMP.BinaryRef`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については、基盤となるドキュメント文字列を参照してください。
