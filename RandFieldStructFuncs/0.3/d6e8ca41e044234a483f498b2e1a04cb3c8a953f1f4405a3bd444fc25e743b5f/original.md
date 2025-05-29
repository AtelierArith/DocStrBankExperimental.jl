```
var(Dᵩ, S, σ=0) -> Vᵩ
```

yields the non-uniform variance `Vᵩ` of a random field having a structure function `Dᵩ` on a support `S` and a piston mode with standard deviation `σ`. The covariance between two nodes of Cartesian coordinates `r` and `r′` is then given by:

```
Cov(r,r′) = (Vᵩ[r] + Vᵩ[r′] - Dᵩ(r - r′))/2
```

if `S[r]` and `S[r′]` are both non-zero, the covariance being assumed to be zero if any of `r` or `r′` is outside the support.
