```
newton_to_monomial!(P::Vector{T}, roots::Vector{T}) where T <: RingElement
```

Converts a polynomial $p$, given as an array of coefficients, in-place from its coefficients given in the Newton basis for the roots $r_0, r_1, \ldots, r_{n-2}$ to the standard monomial basis. In other words, this evaluates $c_0 + c_1(x-r_0) + c_2(x-r_0)(x-r_1) + \ldots + c_{n-1}(x-r_0)(x-r_1)\cdots(x-r_{n-2})$ where $c_i$ are the input coefficients given by $p$.
