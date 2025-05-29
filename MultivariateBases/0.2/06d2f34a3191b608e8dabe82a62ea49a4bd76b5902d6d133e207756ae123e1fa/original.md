```
struct ChebyshevBasisFirstKind{P} <: AbstractChebyshevBasis{P}
    polynomials::Vector{P}
end
```

Orthogonal polynomial with respect to the univariate weight function $w(x) = \frac{1}{\sqrt{1 - x^2}}$ over the interval $[-1, 1]$.
