```julia
struct DrasticAnd <: FuzzyLogic.AbstractAnd
```

Drastic T-norm defining conjuction as $A ∧ B = \min(A, B)$ is $A = 1$ or $B = 1$ and $A ∧ B = 0$ otherwise.
