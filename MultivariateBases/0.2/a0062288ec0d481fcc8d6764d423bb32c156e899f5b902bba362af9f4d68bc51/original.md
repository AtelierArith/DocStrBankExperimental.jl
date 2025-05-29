```
struct LegendreBasis{P} <: AbstractGegenbauerBasis{P}
    polynomials::Vector{P}
end
```

Orthogonal polynomial with respect to the univariate weight function $w(x) = 1$ over the interval $[-1, 1]$.
