```
parameter_value(prefs; [kwargs...])
```

一般的な変数参照のために `parameter_value` を定義します。これは、基盤となる `DispatchVariableRef` に対して `parameter_value` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については基盤となるドキュメントを参照してください。これは自動生成されたラッパーであり、基盤となるメソッドが `kwargs` を使用するかどうかは不明です。
