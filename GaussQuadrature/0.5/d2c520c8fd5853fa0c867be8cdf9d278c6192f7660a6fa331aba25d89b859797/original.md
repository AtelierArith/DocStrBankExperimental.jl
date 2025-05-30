```
x, w = chebyshev(T, n, kind=1, endpt=neither)
```

Returns points `x` and weights `w` for the `n`-point Gauss-Chebyshev rule for the interval `-1 < x < 1` with weight function

```
w(x) = 1 / sqrt(1-x²)   if kind=1
w(x) = sqrt(1-x²)       if kind=2.
```

Use `endpt=left`, `right` or `both` for the left Radau, right Radau or Lobatto rules, respectively.
