```
x, w = jacobi(n, α, β, endpt=neither)
```

Returns points `x` and weights `w` for the `n`-point Gauss-Jacobi rule for the interval `-1 < x < 1` with weight function

```
w(x) = (1-x)ᵅ (1+x)ᵝ.
```

Use `endpt=left`, `right` or `both` for the left Radau, right Radau or Lobatto rules, respectively.
