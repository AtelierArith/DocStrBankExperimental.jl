```julia
struct NilpotentAnd <: FuzzyLogic.AbstractAnd
```

Nilpotent T-norm defining conjuction as $A ∧ B = \min(A, B)$ when $A + B > 1$ and $A ∧ B = 0$ otherwise.
