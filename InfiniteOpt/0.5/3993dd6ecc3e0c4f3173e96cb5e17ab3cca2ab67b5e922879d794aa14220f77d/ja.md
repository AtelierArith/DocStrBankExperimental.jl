```
raw_parameter_valuesc(vref::GeneralVariableRef)
```

一般変数参照のための `raw_parameter_values` を定義します。これは、基盤となる `DispatchVariableRef` に対して `raw_parameter_values` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基盤となるドキュメントを参照してください。
