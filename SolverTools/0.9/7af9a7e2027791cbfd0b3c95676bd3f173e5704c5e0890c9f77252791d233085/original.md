```
active(x, ℓ, u; rtol = 1e-8, atol = 1e-8)
```

Computes the active bounds at x, using tolerance `min(rtol * (uᵢ-ℓᵢ), atol)`. If ℓᵢ or uᵢ is not finite, only `atol` is used.
