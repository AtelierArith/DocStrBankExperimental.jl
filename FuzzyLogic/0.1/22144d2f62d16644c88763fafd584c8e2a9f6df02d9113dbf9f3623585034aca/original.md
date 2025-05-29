```julia
struct BoundedSumOr <: FuzzyLogic.AbstractOr
```

Bounded sum S-norm defining disjunction as $A ∨ B = \min(1, A + B)$.
