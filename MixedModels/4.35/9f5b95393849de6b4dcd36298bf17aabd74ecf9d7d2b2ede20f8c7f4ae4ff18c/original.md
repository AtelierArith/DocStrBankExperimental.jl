```
fixef(m::MixedModel)
```

Return the fixed-effects parameter vector estimate of `m`.

In the rank-deficient case the truncated parameter vector, of length `rank(m)` is returned. This is unlike `coef` which always returns a vector whose length matches the number of columns in `X`.
