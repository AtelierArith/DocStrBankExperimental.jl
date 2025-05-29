```
transformed(d::Distribution)
transformed(d::Distribution, b::Bijector)
```

分布 `d` をバイジェクタ `b` と組み合わせて、`TransformedDistribution` を返します。

バイジェクタが提供されていない場合、すなわち `transformed(d)` が呼び出されると、`transformed(d, bijector(d))` が返されます。
