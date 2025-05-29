```
abstract type AbstractMonomialOrdering end
```

Abstract type for monomial ordering as defined in [CLO13, Definition 2.2.1, p. 55]

Given an ordering `ordering::AbstractMonomialOrdering` and vector of exponents `e1` and `e2`, `cmp(ordering, e1, e2)` returns a negative number if `e1` is before `e2` in the ordering, a positive number if `e2` is before `e1` and 0 if they are equal. For convenience, `ordering(e1, e2)` returns a `Bool` indicating whether `cmp(ordering, e1, e2)` is negative.

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**.
