```
x, w = laguerre(n, α, endpt=neither)
```

Returns points `x` and weights `w` for the `n`-point Gauss-Laguerre rule for the interval `0 < x < ∞` with weight function

```
w(x) = xᵅ exp(-x),   α > -1.
```

Use `endpt=left` for the left Radau rule.
