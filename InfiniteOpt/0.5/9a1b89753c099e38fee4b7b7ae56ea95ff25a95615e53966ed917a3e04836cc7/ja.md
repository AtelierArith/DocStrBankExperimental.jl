```
optimizer_model_constraint(cref::InfOptConstraintRef,
                           key::Val{ext_key_name}; [kwargs...])
```

`cref` に対応する最適化モデルに格納された再定式化制約を返します。これは、カスタム最適化モデルタイプを実装する拡張のために定義する必要があります。主に、`key` 引数を `Val{ext_key_name}` に型付けすることでこれを達成します。必要に応じてキーワード引数を追加できます。
