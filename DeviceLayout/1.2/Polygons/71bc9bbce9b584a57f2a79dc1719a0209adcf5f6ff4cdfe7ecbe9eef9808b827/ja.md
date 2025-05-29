```
sweep_poly(poly::Polygon, displacement::Point)
```

`poly`によって形成された境界を`displacement`によってスイープした結果に対応する`Polygon`を返します。

これは、`poly`の形をしたブラシで塗り、`displacement`に沿って移動させたときに得られる結果です。
