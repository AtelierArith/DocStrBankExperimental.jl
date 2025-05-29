```
struct AbstractGegenbauerBasis{P} <: AbstractMultipleOrthogonalBasis{P}
    polynomials::Vector{P}
end
```

Orthogonal polynomial with respect to the univariate weight function $w(x) = (1 - x^2)^{\alpha - 1/2}$ over the interval $[-1, 1]$.
