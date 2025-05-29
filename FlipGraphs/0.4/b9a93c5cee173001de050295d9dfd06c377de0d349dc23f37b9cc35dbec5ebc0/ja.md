```
is_isomorphic(D1::DeltaComplex, D2::DeltaComplex; kwargs..) :: Bool
```

`D1`が`D2`と同型である場合、頂点や辺の名前を変更しても`true`を返します。また、`labeled_points=false`の場合は点も含まれます。

# 引数

  * `labeled_points :: Bool = true` : labeled_pointsが`false`に設定されている場合、同型は点の名前の変更も含みます。
