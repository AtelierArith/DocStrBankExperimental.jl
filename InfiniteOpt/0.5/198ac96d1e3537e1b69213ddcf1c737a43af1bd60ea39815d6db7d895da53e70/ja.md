```
derivative_method(prefs; [kwargs...])
```

一般的な変数参照のために `derivative_method` を定義します。これは、基盤となる `DispatchVariableRef` に対して `derivative_method` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基盤となるドキュメントを参照してください。これは自動生成されたラッパーであり、基盤となるメソッドが `kwargs` を使用するかどうかは不明です。
