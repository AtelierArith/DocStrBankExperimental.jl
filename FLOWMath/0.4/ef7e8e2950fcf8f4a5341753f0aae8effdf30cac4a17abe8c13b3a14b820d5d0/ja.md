```
second_derivative(spline, x)
```

xにおけるAkimaスプラインの2階導関数を計算します。

**引数**

  * `spline::Akima}`: Akimaスプライン
  * `x::Float`: 評価点

**戻り値**

  * `d2ydx2::Float`: Akimaスプラインを使用したxにおける2階導関数。
