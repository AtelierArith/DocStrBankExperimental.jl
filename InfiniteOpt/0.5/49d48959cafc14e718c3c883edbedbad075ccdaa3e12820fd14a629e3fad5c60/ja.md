```
derivative_constraints(dref::DerivativeRef)::Vector{InfOptConstraintRef}
```

`dref` に直接追加された導関数評価制約のリストを返します。`dref` に関連付けられた `InfiniteModel` に対してです。該当する制約がない場合は空のベクターが返されます。
