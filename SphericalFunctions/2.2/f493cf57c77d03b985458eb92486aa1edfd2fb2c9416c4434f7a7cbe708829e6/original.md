```
ALFcompute(expiβ, nmax)
ALFcompute!(P̄, expiβ, nmax)
ALFcompute(expiβ, nmax, recursion_coefficients)
ALFcompute!(P̄, expiβ, nmax, recursion_coefficients)
```

Compute the "fully normalized" Associated Legendre Functions up to some maximum `n` value `nmax`.

These functions can take a vector P̄, to store the data, stored in order of increasing `m` most rapidly varying and then increasing `n`.  If not supplied, P̄ will be constructed for you and returned.

The optional `recursion_coefficients` argument must be an `ALFRecursionCoefficients`, which stores various constant coefficients used in the recursion.  This object requires more than 3x the memory and more than 20x the time to compute a single P̄ vector without this argument, but passing it will typically speed up the calculation of each P̄ by a factor of 8x or so.  Thus, if you expect to compute P̄ more than a few times, it will take less time to pre-compute those factors, and pass them to this function.

Note that the base real type will be inferred from the (complex) type of `expiβ`.  If present, the base types of `P̄` and `recursion_coefficients` must agree.
