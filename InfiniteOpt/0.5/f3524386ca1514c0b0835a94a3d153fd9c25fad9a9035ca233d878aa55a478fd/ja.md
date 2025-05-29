```
raw_function(prefs; [kwargs...])
```

一般的な変数参照のために `raw_function` を定義します。これは、基盤となる `DispatchVariableRef` に対して `raw_function` が定義されていることに依存しており、そうでない場合は `ArgumentError` がスローされます。詳細については、基盤となるドキュメントを参照してください。これは自動生成されたラッパーであり、基盤となるメソッドが `kwargs` を使用するかどうかは不明です。
