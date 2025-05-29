```
rt = confmap(r, f)
```

Apply the conformal mapping transformation `λ = f(δ)` to the rational transfer function `r(λ)`  and return `rt(δ) = r(f(δ))`. The resulting `rt` inherits the sampling time and variable of `f`.
