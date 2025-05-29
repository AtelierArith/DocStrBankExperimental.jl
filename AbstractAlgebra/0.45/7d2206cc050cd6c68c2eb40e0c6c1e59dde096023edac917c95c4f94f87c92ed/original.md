```
is_univariate_with_data(p::MPolyRingElem)
```

Returns `(true, i)` if $p$ is a univariate polynomial in the `i`-th variable of its parent i.e. involves exactly one variable. If $p$ is constant, `(true, 0)` is returned. Otherwise `(false, 0)` is returned. The result depends on the terms of the polynomial, not simply on the number of variables in the polynomial ring.
