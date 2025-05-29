```
leftinverse(m[, x])
```

Return a left inverse of the given map. This left inverse `mli` is not unique, but in any case it is such that `(mli ∘ m) * x = x` for each `x` in the domain of `m`.

The two-argument function applies the left inverse to the point `x`.
