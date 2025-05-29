```
gradient!(gradient, model::AbstractSem, params)
```

`params` における勾配値を `gradient` に書き込みます。

# 実装

新しい `SemImplied` または `SemLossFunction` 型を実装するには、次のようにメソッドを追加できます。     gradient!(newtype::MyNewType, params, model::AbstractSemSingle)

新しい `AbstractSem` サブタイプを実装するには、次のようにメソッドを追加できます。     gradient!(gradient, model::MyNewType, params)
