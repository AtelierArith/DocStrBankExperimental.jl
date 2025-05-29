```
continued_fraction(x; limit::Int = 0)
```

Return the vector of the first `limit` partial quotients of the continued fraction of $x$. `limit = 0` corresponds to no limit, that is, all partial quotients are generated or as many as can be justified by the precision of the input.
