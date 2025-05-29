```
used_by_constraint(vref::GeneralVariableRef)::Bool
```

`used_by_constraint`を一般変数参照のために定義します。これは、基盤となる`DispatchVariableRef`に対して`used_by_constraint`が定義されていることに依存しており、そうでない場合は`ArgumentError`がスローされます。詳細については基盤となるドキュメントを参照してください。
