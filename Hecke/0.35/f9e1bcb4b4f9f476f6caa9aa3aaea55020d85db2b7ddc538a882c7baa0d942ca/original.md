```
number_field(f::Vector{QQPolyRingElem}, s::VarName="_\$") -> AbsNonSimpleNumField
```

Let $f = (f_1, \ldots, f_n)$ be univariate rational polynomials, then we construct  $K = Q[t_1, \ldots, t_n]/\langle f_1(t_1), \ldots, f_n(t_n)\rangle .$ The ideal must be maximal, however, this is not tested.
