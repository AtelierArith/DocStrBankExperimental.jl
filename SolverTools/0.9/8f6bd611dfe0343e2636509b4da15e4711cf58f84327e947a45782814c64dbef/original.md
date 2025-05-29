```
slope, qs = compute_As_slope_qs!(As, A, s, Fx)
```

Compute `slope = dot(As, Fx)` and `qs = dot(As, As) / 2 + slope`. Use `As` to store `A * s`.
