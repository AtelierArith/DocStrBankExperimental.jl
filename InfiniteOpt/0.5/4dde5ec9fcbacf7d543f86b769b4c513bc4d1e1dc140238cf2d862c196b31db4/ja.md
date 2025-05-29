```
used_by_measure(vref::GeneralVariableRef)::Bool
```

一般変数参照のための `used_by_measure` を定義します。これは、基礎となる `DispatchVariableRef` に対して `used_by_measure` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
