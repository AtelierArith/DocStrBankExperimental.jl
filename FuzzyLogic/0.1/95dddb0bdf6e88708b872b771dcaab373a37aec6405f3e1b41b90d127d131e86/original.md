```julia
struct NilpotentOr <: FuzzyLogic.AbstractOr
```

Nilpotent S-norm defining disjunction as $A ∨ B = \max(A, B)$ when $A + B < 1$ and $A ∧ B = 1$ otherwise.
