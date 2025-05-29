```
terms(A)
```

yields the list (as a tuple) of terms that compose mapping `A`.  If `A` is a sum or a composition of mappings, the list of terms is returned; otherwise, the 1-tuple `(A,)` is returned.

If `A` is sum or a composition of mappings, `Tuple(A)` yields the same result as `terms(A)`.
