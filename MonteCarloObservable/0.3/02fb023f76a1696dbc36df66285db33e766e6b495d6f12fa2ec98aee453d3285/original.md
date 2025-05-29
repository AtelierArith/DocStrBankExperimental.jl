```
iswithinerrorbars(a, b, δ[, print=false])
```

Checks whether numbers `a` and `b` are equal up to given error `δ`. Will print `x ≈ y + k·δ` for `print=true`.

Is equivalent to `isapprox(a,b,atol=δ,rtol=zero(b))`.
