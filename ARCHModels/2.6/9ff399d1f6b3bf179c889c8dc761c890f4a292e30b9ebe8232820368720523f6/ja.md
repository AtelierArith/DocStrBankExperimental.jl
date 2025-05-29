```
selectmodel(::Type{<:ARMA}, data; kwargs...)  -> UnivariateARCHModel
```

`data` に対して複数の `ARMA{p, q}` モデルをフィットし、[BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion) を最小化するモデルを返します。

# キーワード引数:

  * `dist=StdNormal`: 誤差分布。
  * `minlags=1`: 各パラメータの `VS` で試す最小ラグ長。
  * `maxlags=3`: 各パラメータの `VS` で試す最大ラグ長。
  * `criterion=bic`: `UnivariateARCHModel` を受け取り、最小化する基準を返す関数。
  * `show_trace=false`: 推定された各モデルの `criterion` を画面に表示します。
  * `algorithm=BFGS(), autodiff=:forward, kwargs...`: 最適化器に渡されます。
