```
has_derivative_constraints(dref::DerivativeRef)::Bool
```

`dref`が`InfiniteModel`内で評価され、`InfiniteModel`に追加された導関数制約を持っているかどうかを示す`Bool`を返します。これは、そのような制約が最適化モデルに追加されたかどうかを示すものではありません。したがって、通常の使用（すなわち、`evaluate`を使用しない場合）では、常に`false`を返すべきです。
