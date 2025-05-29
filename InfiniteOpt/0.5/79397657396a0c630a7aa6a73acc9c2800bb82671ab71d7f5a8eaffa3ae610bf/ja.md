```
optimizer_model_variable(vref::GeneralVariableRef, key::Val{ext_key_name};
                         [kwargs...])
```

`vref` に対応する最適化モデルに格納されている再定式化変数を返します。これは、カスタム最適化モデルタイプを実装する拡張のために定義する必要があります。基本的には、`key` 引数を `Val{ext_key_name}` に型付けすることで実現されます。必要に応じてキーワード引数を追加できます。
