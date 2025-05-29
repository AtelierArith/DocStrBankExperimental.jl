```
isequivalent(rn1::ReactionSystem, rn2::ReactionSystem; ignorenames = true,
    debug = false)
```

Tests whether the underlying species, parameters and reactions are the same in the two [`ReactionSystem`](@ref)s. Ignores the names of the systems in testing equality.

Notes:

  * *Does not* currently simplify rates, so a rate of `A^2+2*A+1` would be considered   different than `(A+1)^2`.
  * `ignorenames = false` is used when checking equality of sub and parent systems.
  * Does not check that `parent` systems are the same.
  * Pass `debug = true` to print out the field that caused the two systems to be considered   different.
