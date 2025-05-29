```
coulombs!(F, F′, G, G′, x, η, ℓ)
```

Main routine that computes the continued fractions and the recurrence relations to generate the regular functions $F_\ell(\eta,x)$ and $F_\ell'(\eta,x)$ and the irregular functions $G_\ell(\eta,x)$ and $G_\ell'(\eta,x)$ (computation of the latter can be elided by passing `nothing` for `G` and `G′`).
