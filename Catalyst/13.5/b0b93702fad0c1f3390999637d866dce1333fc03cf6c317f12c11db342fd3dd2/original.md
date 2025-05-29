```
isequivalent(rn1::ReactionSystem, rn2::ReactionSystem; ignorenames = true)
```

Tests whether the underlying species, parameters and reactions are the same in the two [`ReactionSystem`](@ref)s. Ignores the names of the systems in testing equality.

Notes:

  * *Does not* currently simplify rates, so a rate of `A^2+2*A+1` would be   considered different than `(A+1)^2`.
  * Does not include `defaults` in determining equality.
