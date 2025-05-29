```
observability(A, C; atol, rtol)
```

Check for observability of the pair `(A, C)` or `sys` using the PHB test.

The return value contains the field `isobservable` which is `true` if the rank condition is met at all eigenvalues of `A`, and `false` otherwise. The returned structure also contains the rank and smallest singular value at each individual eigenvalue of `A` in the fields `ranks` and `sigma_min`.
