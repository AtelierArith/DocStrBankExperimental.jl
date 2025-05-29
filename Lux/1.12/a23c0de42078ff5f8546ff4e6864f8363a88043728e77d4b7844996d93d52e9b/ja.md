```
recursive_eltype(x, unwrap_ad_types = Val(false))
```

ネストされた構造 `x` の要素型を再帰的に決定します。これは `fmap(Lux.Utils.eltype, x)` を行うことと同等ですが、この実装は一般的なケースに対して型安定なコードを使用します。

`nothing` や `Val` 型のような曖昧な入力に対しては、要素型として `Bool` を返します。

`unwrap_ad_types` が `Val(true)` に設定されている場合、トレースおよび演算子オーバーロードされたAD（ForwardDiff、ReverseDiff、Tracker）に対して、この関数はアンラップされた値の要素型を返します。
