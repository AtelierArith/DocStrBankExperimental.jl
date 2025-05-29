```
monomial_to_newton!(P::Vector{T}, roots::Vector{T}) where T <: RingElement
```

Converts a polynomial $p$, given as an array of coefficients, in-place from its coefficients given in the standard monomial basis to the Newton basis for the roots $r_0, r_1, \ldots, r_{n-2}$. In other words, this determines output coefficients $c_i$ such that $c_0 + c_1(x-r_0) + c_2(x-r_0)(x-r_1) + \ldots + c_{n-1}(x-r_0)(x-r_1)\cdots(x-r_{n-2})$ is equal to the input polynomial.
