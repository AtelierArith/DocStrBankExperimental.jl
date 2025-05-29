```
gcd(p1::StandardBasisPolynomial, p2::StandardBasisPolynomial; method=:euclidean, kwargs...)
```

Find the greatest common divisor.

By default, uses the Euclidean division algorithm (`method=:euclidean`), which is susceptible to floating point issues.

Passing `method=:noda_sasaki` uses scaling to circumvent some of these.

Passing `method=:numerical` will call the internal method `NGCD.ngcd` for the numerical gcd. See the docstring of `NGCD.ngcd` for details.
