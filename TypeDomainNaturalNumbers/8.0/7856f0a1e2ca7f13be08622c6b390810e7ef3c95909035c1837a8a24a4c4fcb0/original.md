```
NonnegativeInteger
```

Nonnegative integers in the type domain.

There are two type parameters:

  * The first type parameter, `N`, is an `Int` value, the value of the nonnegative integer.
  * The second type parameter supertypes `NTuple{N}` and subtypes `Tuple`. For small-enough `N` the length is exactly `N`. Ideally it would always be exactly `N`, but it may not be for compiler efficiency reasons.
