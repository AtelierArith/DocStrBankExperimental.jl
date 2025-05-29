```
fit(AbstractOrdinalMultinomialModel, X, y, link, solver)
```

最大尤度推定による順序多項モデルの適合。

# 入力

  * `y::Vector`: 値が `1,...,J` の整数ベクトル。
  * `X::Matrix`: 切片を除く `n x p` の共変量行列。
  * `link::GLM.Link`: `LogitLink()`, `ProbitLink()`, `CauchitLink()`, または `CloglogLink()`。
  * `solver`: `Ipopt.Optimizer()` または `NLopt.Optimizer()` のインスタンス（デフォルト）。

# 出力

  * `dd:OrdinalMultinomialModel`: `OrdinalMultinomialModel` 型。
