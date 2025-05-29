```
map(fn, p::AbstractPolynomial, args...)
```

Transform coefficients of `p` by applying a function (or other callables) `fn` to each of them.

You can implement `real`, etc., to a `Polynomial` by using `map`. The type of `p` may narrow using this function.
