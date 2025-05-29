```julia
SemiInfRational(A, L)

```

The domian transformed to  `[A, Inf)` (when `L > 0`) or `(-Inf,A]` (when `L < 0`) using $y = A + L ⋅ (1 + x) / (1 - x)$.

When used with Chebyshev polynomials, also known as a “rational Chebyshev” basis.

# Example mappings for the domain $(-1,1)$

  * $-1/2 ↦ A + L / 3$
  * $0 ↦ A + L$
  * $1/2 ↦ A + 3 ⋅ L$
