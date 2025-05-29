```
quadgp(weight::Function,lb::Real,ub::Real,N::Int=10;quadrature::Function=clenshaw_curtis,bnd::Float64=Inf)
```

general purpose quadrature based on Gautschi, "Orthogonal Polynomials: Computation and Approximation", Section 2.2.2, pp. 93-95

Compute the `N`-point quadrature rule for `weight` with support (`lb`, `ub`). The quadrature rule can be specified by the keyword `quadrature`. The keyword `bnd` sets the numerical value for infinity.
