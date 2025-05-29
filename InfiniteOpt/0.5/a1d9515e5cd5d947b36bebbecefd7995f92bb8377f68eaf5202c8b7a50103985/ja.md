```
JuMP.fix(vref::GeneralVariableRef, value::Real; force::Bool = false)::Nothing
```

一般的な変数参照のための `JuMP.fix` を定義します。これは、基礎となる `DispatchVariableRef` に対して `JuMP.fix` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基礎となるドキュメントを参照してください。
