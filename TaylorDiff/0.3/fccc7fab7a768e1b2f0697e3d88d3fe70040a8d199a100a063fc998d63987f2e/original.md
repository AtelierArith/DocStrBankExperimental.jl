```
TaylorScalar{T, P}
```

Representation of Taylor polynomials.

# Fields

  * `value::T`: zeroth order coefficient
  * `partials::NTuple{P, T}`: i-th element of this stores the i-th derivative
