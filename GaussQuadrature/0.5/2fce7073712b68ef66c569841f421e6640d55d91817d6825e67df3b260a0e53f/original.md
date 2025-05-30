```
x, w = legendre(T, n, endpt=neither)
```

Returns points `x` and weights `w` for the `n`-point Gauss-Legendre rule for the interval `-1 < x < 1` with weight function `w(x) = 1`.

Use `endpt=left`, `right` or `both` for the left Radau, right Radau or Lobatto rules, respectively.
