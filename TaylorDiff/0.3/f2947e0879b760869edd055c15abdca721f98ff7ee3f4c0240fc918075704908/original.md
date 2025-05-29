```
TaylorArray{T, N, A, P}
```

Representation of Taylor polynomials in array mode.

# Fields

  * `value::A`: zeroth order coefficient
  * `partials::NTuple{P, A}`: i-th element of this stores the i-th derivative
