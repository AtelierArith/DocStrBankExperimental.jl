```
x, w = legendregauss(T, n, endpoint::EndPoint=OneDimensionalNodes.NeitherEndPoint())
```

Returns points `x` and weights `w` for the `n`-point Gauss-Legendre rule for the interval `-1 < x < 1` with weight function `w(x) = 1`.

Use `endpoint=LeftEndPoint()`, `RightEndPoint()` or `BothEndPoints()` for the left Radau, right Radau, or Lobatto rules, respectively.
