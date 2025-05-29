```julia
struct LukasiewiczAnd <: FuzzyLogic.AbstractAnd
```

Lukasiewicz T-norm defining conjuction as $A ∧ B = \max(0, A + B - 1)$.
