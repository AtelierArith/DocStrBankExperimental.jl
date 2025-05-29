```
parameter_refsc(vref::GeneralVariableRef)
```

一般変数参照のための `parameter_refs` を定義します。これは、基盤となる `DispatchVariableRef` に対して `parameter_refs` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基盤となるドキュメント文字列を参照してください。
