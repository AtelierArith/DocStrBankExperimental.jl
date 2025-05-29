```
polr(formula, df, link, solver=NLoptSolver(algorithm=:LD_SLSQP, maxeval=4000))
polr(X, y, link, solver=NLoptSolver(algorithm=:LD_SLSQP, maxeval=4000))
```

最大尤度推定による順序多項モデルの適合。

# 位置引数

  * `formula::Formula`: 応答と回帰変数を指定するモデル式。
  * `df::DataFrame`: データフレーム。応答変数は1から始まる整数値を取るべきです。
  * `y::Vector`: `1,...,J`の値を取る整数ベクトル。
  * `X::Matrix`: 切片を除く`n x p`の共変量行列。
  * `link::GLM.Link`: `LogitLink()`（デフォルト）、`ProbitLink()`、`CauchitLink()`、または`CloglogLink()`。
  * `solver`: `Ipopt.Optimizer()`または`NLopt.Optimizer()`のインスタンス（デフォルト）。

# キーワード引数

  * `wts::AbstractVector=similar(X, 0)`: 観測重み。

# 出力

  * `dd:PolrModel`: `PolrModel`型。
