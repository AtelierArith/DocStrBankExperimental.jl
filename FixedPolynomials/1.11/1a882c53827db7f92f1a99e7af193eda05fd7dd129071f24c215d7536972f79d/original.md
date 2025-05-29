```
homogenize(p::Polynomial [, variable = :x0])
```

Makes `p` homogenous, if `ishomogenized(p)` is `true` this is just the identity. The homogenization variable will always be considered as the first variable of the polynomial.
