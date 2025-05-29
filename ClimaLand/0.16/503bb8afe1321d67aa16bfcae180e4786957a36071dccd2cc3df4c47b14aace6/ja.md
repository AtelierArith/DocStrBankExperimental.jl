```
make_exp_tendency(model::AbstractModel)
```

`exp_tendency`を返し、補助変数を更新し、明示的にステップされた変数の予測状態を更新します。

`compute_exp_tendency!`はSciMLBase.jlソルバーと互換性があるべきです。
