```
riemann_plot!(f, a, b, n; method="method", fill, kwargs...)
riemann_plot(f, a, b, n; method="method", fill, kwargs...)
```

Add visualization of riemann sum in a layer.

  * `method`: one of `right`, `left`, `trapezoid`, `simpsons`
  * `fill`: to specify fill color, something like `("green", 0.25, 0)` will fill in green with an alpha transparency.
