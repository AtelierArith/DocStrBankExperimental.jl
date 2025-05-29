```
static_operator(op::AbstractOperator)
```

`op`の現在の時刻における静的（時間依存でない）表現を返します。これは時間依存性を取り除き、演算子の非遅延行列表現を取得するために使用できます。

例えば：`sparse(static_operator(op(t))` は時刻`t`における`op`の疎行列表現を返します。
