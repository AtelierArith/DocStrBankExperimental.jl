```
controllability(A, B; atol, rtol)
controllability(sys; atol, rtol)
```

Check for controllability of the pair `(A, B)` or `sys` using the PHB test.

The return value contains the field `iscontrollable` which is `true` if the rank condition is met at all eigenvalues of `A`, and `false` otherwise. The returned structure also contains the rank and smallest singular value at each individual eigenvalue of `A` in the fields `ranks` and `sigma_min`.

Technically, this function checks for controllability from the origin, also called reachability.
