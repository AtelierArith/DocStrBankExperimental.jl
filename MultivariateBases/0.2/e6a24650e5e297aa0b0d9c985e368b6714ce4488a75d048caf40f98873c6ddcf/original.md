```
struct LaguerreBasis{P} <: AbstractMultipleOrthogonalBasis{P}
    polynomials::Vector{P}
end
```

Orthogonal polynomial with respect to the univariate weight function $w(x) = \exp(-x)$ over the interval $[0, \infty]$.
