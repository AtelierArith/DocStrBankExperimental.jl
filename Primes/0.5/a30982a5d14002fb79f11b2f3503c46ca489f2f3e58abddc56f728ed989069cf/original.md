```
eachfactor(n::Integer)->FactorIterator
```

Returns a lazy iterator of factors of `n` in `(factor, multiplicity)` pairs. This can be very useful for computing multiplicative functions since for small numbers (e.g. numbers with no factor `>2^16`), allocating the storage required for `factor(n)` can introduce significant overhead.
