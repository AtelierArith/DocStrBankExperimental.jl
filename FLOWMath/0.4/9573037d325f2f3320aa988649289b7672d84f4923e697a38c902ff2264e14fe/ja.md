```
derivative(spline, x)
```

xにおけるAkimaスプラインの導関数を計算します。

**引数**

  * `spline::Akima}`: Akimaスプライン
  * `x::Float`: 評価点

**戻り値**

  * `dydx::Float`: Akimaスプラインを使用したxにおける導関数。
