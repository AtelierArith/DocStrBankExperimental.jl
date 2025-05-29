```
SinkhornEpsilonScaling(algorithm::Sinkhorn; factor=1//2, steps=5)
```

エントロピー正則化最適輸送問題を解くためのεスケーリングSinkhornアルゴリズムを構築します。

この関数は、指定されたSinkhorn `algorithm`を使用し、スケーリングファクター`factor`を持つ`steps`のεスケーリングステップを実行します。エントロピー正則化最適輸送を順次解決し、正則化パラメータは次のようになります。

$$
\varepsilon_i := \varepsilon \lambda^{i-k}, \qquad (i = 1,\ldots,k),
$$

ここで、$\lambda$はスケーリングファクター、$k$はスケーリングステップの数です。
