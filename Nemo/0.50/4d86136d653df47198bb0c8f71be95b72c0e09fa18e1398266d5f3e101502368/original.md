```
unique_integer(x::RealPolyRingElem)
```

Return a tuple `(t, z)` where $t$ is `true` if there is a unique integer contained in each of the coefficients of $x$, otherwise sets $t$ to `false`. In the former case, $z$ is set to the integer polynomial.
