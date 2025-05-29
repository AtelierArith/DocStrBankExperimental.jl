```
gradient(spline, x)
```

xにおけるAkimaスプラインの勾配を計算します。

**引数**

  * `spline::Akima}`: Akimaスプライン
  * `x::Vector{Float}`: 評価点

**戻り値**

  * `dydx::Vector{Float}`: Akimaスプラインを使用したxにおける勾配。
