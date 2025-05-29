```
riemann_plot!(f, a, b, n; method="method", fill, kwargs...)
riemann_plot(f, a, b, n; method="method", fill, kwargs...)
```

リーマン和の視覚化をレイヤーに追加します。

  * `method`: `right`、`left`、`trapezoid`、`simpsons` のいずれか
  * `fill`: 塗りつぶしの色を指定します。例えば `("green", 0.25, 0)` のように、緑色でアルファ透明度を持たせて塗りつぶします。
