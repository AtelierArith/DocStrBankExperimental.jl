```
fit(GeneralizedEstimatingEquationsModel, X, y, g, l, v, [c = IndependenceCor()]; <keyword arguments>)
```

一般化推定方程（GEE）を使用してデータに一般化線形モデルを適合させます。このインターフェースはGEEの「準似然」フレームワークを強調しており、分布/ファミリーに言及することなく、リンクおよび分散関数の直接的な指定を必要とします。
