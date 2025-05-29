```
coeff(a::T, vars::Vector{T}, exps::Vector{Int}) where T <: MPolyRingElem
```

Return the "coefficient" of $a$ (as a multivariate polynomial in the same ring) of the monomial consisting of the product of the given variables to the given exponents (note that not all variables need to appear and the exponents can be zero). E.g. `coeff(f, [x, z], [0, 2])` returns the coefficient of $x^0*z^2$ in the polynomial $f$.
