```
struct Poly{PB<:AbstractPolynomialBasis} <: AbstractPoly
    polynomial_basis::PB
end
```

Polynomial variable $v^\top p$ where $v$ is a vector of new decision variables and $p$ is a vector of polynomials for the basis `polynomial_basis`.
