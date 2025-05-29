```
objective!(model::AbstractSem, params)
```

`params`での目的値を返します。モデルオブジェクトは変更可能です。

# 実装

新しい `SemImplied` または `SemLossFunction` サブタイプを実装するには、次のメソッドを追加する必要があります。     objective!(newtype::MyNewType, params, model::AbstractSemSingle)

新しい `AbstractSem` サブタイプを実装するには、次のメソッドを追加する必要があります。     objective!(model::MyNewType, params)
