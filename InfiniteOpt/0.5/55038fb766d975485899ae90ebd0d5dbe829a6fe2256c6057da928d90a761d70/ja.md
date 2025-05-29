```
optimizer_model_expression(expr, key::Val{ext_key_name}; [kwargs...])
```

`expr` に対応する最適化モデルに格納されている再定式化式を返します。これは、カスタム最適化モデルタイプを実装する拡張のために定義する必要があります。主に、`key` 引数を `Val{ext_key_name}` に型付けすることで実現されます。必要に応じてキーワード引数を追加できます。`expr` が `GeneralVariableRef` の場合、これは単に `optimizer_model_variable` にディスパッチされます。
