```
lowest_terms(pq::AbstractRationalFunction, method=:numerical)
```

Find GCD of `(p,q)`, `u`, and return `(p÷u)//(q÷u)`. Commonly referred to as lowest terms.

  * `method`: passed to `gcd(p,q)`
  * `kwargs`: passed to `gcd(p,q)`

By default, `AbstractRationalFunction` types do not cancel common factors. This method will numerically cancel common factors, returning the normal form, canonicalized here by `q[end]=1`. The result and original may be considered equivalent as rational expressions, but different when seen as functions of the indeterminate.
