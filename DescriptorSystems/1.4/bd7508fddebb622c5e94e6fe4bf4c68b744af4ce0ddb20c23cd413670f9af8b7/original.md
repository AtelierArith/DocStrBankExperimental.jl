```
Rt = confmap(R, f)
```

Apply elementwise the conformal mapping transformation `λ = f(δ)` to the rational transfer function matrix `R(λ)`  and return `Rt(δ) = R(f(δ))`. The resulting elements of `Rt` inherit the sampling time and variable of `f`.
