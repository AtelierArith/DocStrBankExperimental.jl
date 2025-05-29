```
Forcing(array::FlavorOfFTS)
```

モデルフィールドの傾向に追加できる`FieldTimeSeries`による`Forcing`を返します。

Forcingは`fts[i, j, k, Time(clock.time)]`を呼び出すことによって計算されるため、`FieldTimeSeries`は`grid`の空間次元を持っている必要があります。
