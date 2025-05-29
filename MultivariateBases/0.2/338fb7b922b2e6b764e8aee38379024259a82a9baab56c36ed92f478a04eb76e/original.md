```
struct PhysicistsHermiteBasis{P} <: AbstractHermiteBasis{P}
    polynomials::Vector{P}
end
```

Orthogonal polynomial with respect to the univariate weight function $w(x) = \exp(-x^2)$ over the interval $[-\infty, \infty]$.
