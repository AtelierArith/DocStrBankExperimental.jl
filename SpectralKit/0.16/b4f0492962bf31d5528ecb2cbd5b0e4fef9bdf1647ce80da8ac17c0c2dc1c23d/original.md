```julia
InfRational(A, L)

```

The domain transformed to `(-Inf, Inf)` using $y = A + L ⋅ x / √(1 - x^2)$, with `L > 0`.

# Example mappings (for domain $(-1,1)$)

  * $0 ↦ A$
  * $±0.5 ↦ A ± L / √3$
