```
is_univariate(p::MPolyRingElem)
```

Returns `true` if $p$ is a univariate polynomial, i.e. involves at most one variable (thus constant polynomials are considered univariate), and `false` otherwise. The result depends on the terms of the polynomial, not simply on the number of variables in the polynomial ring.
