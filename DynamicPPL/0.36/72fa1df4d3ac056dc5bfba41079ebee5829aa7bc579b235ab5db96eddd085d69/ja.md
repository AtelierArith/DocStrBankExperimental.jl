```
(model::Model)([rng, varinfo, sampler, context])
```

`sampler`を使用して`model`からサンプルを取得し、乱数生成器`rng`と`context`を使用して、サンプルと対数結合確率を`varinfo`に格納します。

このメソッドは`varinfo`の対数結合確率をリセットし、`sampler`の評価数を増加させます。
