```
rightinverse(m[, x])
```

Return a right inverse of the given map. This right inverse `mri` is not unique, but in any case it is such that `(m ∘ mri) * y = y` for each `y` in the range of `m`.

The two-argument function applies the right inverse to the point `x`.
