```
ExplicitTableau(; a, b, c)
```

A wrapper for an explicit Butcher tableau. Only `a` is a required argument; the default value for `b` assumes that the algorithm is FSAL (first same as last), and the default value for `c` assumes that it is internally consistent. The matrix `a` must be strictly lower triangular.
