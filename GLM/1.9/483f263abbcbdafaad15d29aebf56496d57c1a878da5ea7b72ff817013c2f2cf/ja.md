```
cooksdistance(obj::LinearModel)
```

線形モデル `obj` の各観測値に対する [クックの距離](https://en.wikipedia.org/wiki/Cook%27s_distance) を計算し、各データポイントの影響の推定値を提供します。現在、重みなしの線形モデルにのみ実装されています。
