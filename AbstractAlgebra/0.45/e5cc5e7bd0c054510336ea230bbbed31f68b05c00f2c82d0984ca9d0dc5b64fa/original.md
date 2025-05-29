```
coeff(a::MPolyRingElem{T}, vars::Vector{Int}, exps::Vector{Int}) where T <: RingElement
```

Return the "coefficient" of $a$ (as a multivariate polynomial in the same ring) of the monomial consisting of the product of the variables of the given indices raised to the given exponents (note that not all variables need to appear and the exponents can be zero). E.g. `coeff(f, [1, 3], [0, 2])` returns the coefficient of $x^0*z^2$ in the polynomial $f$ (assuming variables $x, y, z$ in that order).
